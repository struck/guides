Protocol
========

General development and architecture guidelines.

- Use [Homebrew](http://mxcl.github.io/homebrew/) for OSX packages and binaries 
- Prefer [Postgres.app](http://postgresapp.com/) to other installation methods of Postgres. 
- Prefer [Mamp](http://www.mamp.info/) to other installation methods of Mysql or Php.

Git / Version Control
---------------------

- Use Git and Github.
- Don't check sensitive values or data into version control.
- Name repos using snake_case, not dashed-case or CamelCase, and when possible in the case 
  of web apps, name repos after the domain at which they will be hosted. 
- Name branches using snake_case, not dashed-case or CamelCase. 
- Perform work in a feature branch.
- Delete feature branches from remotes after those branches are irrelevant.
- Write [verbose and descriptive commit messages](http://goo.gl/w11us).
- Tag major releases of a web app.

Ruby
----

- Use either [rbenv] or [rvm] for Ruby version management, expect either in new apps.
- Specify a ruby version.
- Keep ruby versions in sync between `.ruby-version`, `.rvmrc', and `Gemfile`
- Prefer to lock projects to a specific ruby version such as `1.9.2` or `1.9.3` 
  as opposed to patch versions such as `1.9.2p290`.
- Prefer [Unicorn](https://github.com/defunkt/unicorn) over Thin and Webrick.
- Use Bundle for any type of Ruby app.

Project Environments and Processes
----------------------------------

- Run development environments from your localhost machine.
- Expect project ENV variables to define portable and sensitive values.
- Create/Expect a Env.example to showcase the possible configurations, but don't populate an example with sensitive values. (substitute things like private keys with "xxxxxxxxxxx")
- Prefer the [Procfile format](http://www.neilmiddleton.com/the-procfile-is-your-friend/) over direct process management. (Ruby: [Foreman](http://ddollar.github.io/foreman/), Shell: [shoreman](https://github.com/hecticjeff/shoreman), Python: [Honcho](https://honcho.readthedocs.org/en/latest/), Node.js: [Norman](https://github.com/josh/norman))
- Don't check `.env` files into version control.
- Use ENV's for system configuration, such as the local path to a ssh key required for deployment or similar tasks or the path to a particular global sdk. This allows each development machine to customize where dependencies live.

Shared Services
---------------

* Name storage buckets after the domain that will be used to access them. 
  (Example: `assets.struck.com`, not `struck-assets`)
* Don't store files by hand on a S3 (or other storage) bucket that is used 
  to store assets dynamically.
* Don't share data-store services between applications. (Such as using one 
  Redis host for two websites)

Data
----

* Prefer Postgres over Mysql
* Use Memecached if only caching is needed, use Redis if additional data-store is needed 
  beyond caching.

