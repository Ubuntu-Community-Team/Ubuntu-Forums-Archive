---
title: "permission problems."
date: 2008-01-02
forum: General Help
---

### Post by JESii on 2008-01-02
I am stuck on a "permission denied" error, while trying to install/test Rails on my kubuntu machine (recently installed).

I craeted my Rails application directory in /var/railsapps and chown'd and chmod'd (775) it to read:
  drwxrwxr-x  3 www-data www-data 4096 2008-01-02 09:38 railsapps

My userid is a member of the www-data group:
 jseidel@EDP15:/var$ groups jseidel
 jseidel@EDP15:/var$ jseidel adm dialout cdrom floppy audio dip www-data video plugdev scanner netdev lpadmin powerdev admin

Yet when I attempt to create a rails project, it fails with 'permission denied':
  jseidel@EDP15:/var/railsapps$ rails test2
        create
  Permission denied - /var/railsapps/test2

The only way I can get this to work is by doing:
  chmod 777 railsapps
but that means that anyone can read/write/execute...

What am I doing wrong here?

Thanks much

---

### Post by davidshere on 2008-01-02
My guess is that it's trying to create the project as root.  Try

```
sudo rails test2
```

Just an idea.  I'm not familiar with rails.   I wrote a bunch of stuff about permissions in /var, but it looks like you've already done that.

---

### Post by JESii on 2008-01-02
Thanks, David... AFIK, Rails operates just like any other application and doesn't attempt anything via root.  I did try the sudo rails test and that does work, but I don't think I should have to use root to do simple application development.

Cheers...jon

---

### Post by davidshere on 2008-01-02
How did you install rails?  Through the Ubuntu repositories?  When I tried this it didn't create a directory called "/var/railsapps".  All seemed to work fine.

```
david@sabre:~$ sudo apt-get install rails
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  irb1.8 liberb-ruby libmocha-ruby1.8 libreadline-ruby1.8 libredcloth-ruby1.8 libruby1.8 libsqlite3-ruby1.8 rake rdoc rdoc1.8 ruby ruby1.8
Suggested packages:
  libapache2-mod-ruby libapache-mod-ruby libapache2-mod-fcgid libfcgi-ruby1.8 graphviz ruby1.8-examples ri1.8
Recommended packages:
  irb
The following NEW packages will be installed:
  irb1.8 liberb-ruby libmocha-ruby1.8 libreadline-ruby1.8 libredcloth-ruby1.8 libruby1.8 libsqlite3-ruby1.8 rails rake rdoc rdoc1.8 ruby
  ruby1.8
0 upgraded, 13 newly installed, 0 to remove and 0 not upgraded.
Need to get 4182kB of archives.
After unpacking 25.8MB of additional disk space will be used.
Do you want to continue [Y/n]? 
Get:1 http://us.archive.ubuntu.com hardy/main libruby1.8 1.8.6.111-2ubuntu1 [1385kB]
Get:2 http://us.archive.ubuntu.com hardy/main ruby1.8 1.8.6.111-2ubuntu1 [24.9kB]                                                             
Get:3 http://us.archive.ubuntu.com hardy/universe libreadline-ruby1.8 1.8.6.111-2ubuntu1 [10.5kB]                                             
Get:4 http://us.archive.ubuntu.com hardy/universe irb1.8 1.8.6.111-2ubuntu1 [73.2kB]                                                          
Get:5 http://us.archive.ubuntu.com hardy/universe liberb-ruby 2.0.4+ruby1.8.2-1 [3536B]                                                       
Get:6 http://us.archive.ubuntu.com hardy/universe libmocha-ruby1.8 0.5.3-1 [16.2kB]                                                           
Get:7 http://us.archive.ubuntu.com hardy/universe libredcloth-ruby1.8 3.0.99.0.svn.20060519-1 [68.0kB]                                        
Get:8 http://us.archive.ubuntu.com hardy/universe libsqlite3-ruby1.8 1.2.1-1 [48.6kB]                                                         
Get:9 http://us.archive.ubuntu.com hardy/main ruby 1.8.2-1 [19.0kB]                                                                           
Get:10 http://us.archive.ubuntu.com hardy/universe rake 0.7.3-1ubuntu1 [117kB]                                                                
Get:11 http://us.archive.ubuntu.com hardy/universe rdoc1.8 1.8.6.111-2ubuntu1 [125kB]                                                         
Get:12 http://us.archive.ubuntu.com hardy/universe rdoc 1.8.2-1 [3852B]                                                                       
Get:13 http://us.archive.ubuntu.com hardy/universe rails 1.2.6-1 [2288kB]                                                                     
Fetched 4182kB in 28s (148kB/s)                                                                                                               
Selecting previously deselected package libruby1.8.
(Reading database ... 144709 files and directories currently installed.)
Unpacking libruby1.8 (from .../libruby1.8_1.8.6.111-2ubuntu1_i386.deb) ...
Selecting previously deselected package ruby1.8.
Unpacking ruby1.8 (from .../ruby1.8_1.8.6.111-2ubuntu1_i386.deb) ...
Selecting previously deselected package libreadline-ruby1.8.
Unpacking libreadline-ruby1.8 (from .../libreadline-ruby1.8_1.8.6.111-2ubuntu1_i386.deb) ...
Selecting previously deselected package irb1.8.
Unpacking irb1.8 (from .../irb1.8_1.8.6.111-2ubuntu1_all.deb) ...
Selecting previously deselected package liberb-ruby.
Unpacking liberb-ruby (from .../liberb-ruby_2.0.4+ruby1.8.2-1_all.deb) ...
Selecting previously deselected package libmocha-ruby1.8.
Unpacking libmocha-ruby1.8 (from .../libmocha-ruby1.8_0.5.3-1_all.deb) ...
Selecting previously deselected package libredcloth-ruby1.8.
Unpacking libredcloth-ruby1.8 (from .../libredcloth-ruby1.8_3.0.99.0.svn.20060519-1_all.deb) ...
Selecting previously deselected package libsqlite3-ruby1.8.
Unpacking libsqlite3-ruby1.8 (from .../libsqlite3-ruby1.8_1.2.1-1_i386.deb) ...
Selecting previously deselected package ruby.
Unpacking ruby (from .../archives/ruby_1.8.2-1_all.deb) ...
Selecting previously deselected package rake.
Unpacking rake (from .../rake_0.7.3-1ubuntu1_all.deb) ...
Selecting previously deselected package rdoc1.8.
Unpacking rdoc1.8 (from .../rdoc1.8_1.8.6.111-2ubuntu1_all.deb) ...
Selecting previously deselected package rdoc.
Unpacking rdoc (from .../archives/rdoc_1.8.2-1_all.deb) ...
Selecting previously deselected package rails.
Unpacking rails (from .../archives/rails_1.2.6-1_all.deb) ...
Setting up libruby1.8 (1.8.6.111-2ubuntu1) ...

Setting up ruby1.8 (1.8.6.111-2ubuntu1) ...
Setting up libreadline-ruby1.8 (1.8.6.111-2ubuntu1) ...
Setting up irb1.8 (1.8.6.111-2ubuntu1) ...

Setting up liberb-ruby (2.0.4+ruby1.8.2-1) ...
Setting up libmocha-ruby1.8 (0.5.3-1) ...
Setting up libredcloth-ruby1.8 (3.0.99.0.svn.20060519-1) ...
Setting up libsqlite3-ruby1.8 (1.2.1-1) ...
Setting up ruby (1.8.2-1) ...
Setting up rake (0.7.3-1ubuntu1) ...
Setting up rdoc1.8 (1.8.6.111-2ubuntu1) ...
Setting up rdoc (1.8.2-1) ...
Setting up rails (1.2.6-1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
david@sabre:~$ rails
david@sabre:~$ rails test
      create  
      create  app/controllers
      create  app/helpers
      create  app/models
      create  app/views/layouts
      create  config/environments
      create  components
      create  db
      create  doc
      create  lib
      create  lib/tasks
      create  log
      create  public/images
      create  public/javascripts
      create  public/stylesheets
      create  script/performance
      create  script/process
      create  test/fixtures
      create  test/functional
      create  test/integration
      create  test/mocks/development
      create  test/mocks/test
      create  test/unit
      create  vendor
      create  vendor/plugins
      create  tmp/sessions
      create  tmp/sockets
      create  tmp/cache
      create  tmp/pids
      create  Rakefile
      create  README
      create  app/controllers/application.rb
      create  app/helpers/application_helper.rb
      create  test/test_helper.rb
      create  config/database.yml
      create  config/routes.rb
      create  public/.htaccess
      create  config/boot.rb
      create  config/environment.rb
      create  config/environments/production.rb
      create  config/environments/development.rb
      create  config/environments/test.rb
      create  script/about
      create  script/breakpointer
      create  script/console
      create  script/destroy
      create  script/generate
      create  script/performance/benchmarker
      create  script/performance/profiler
      create  script/process/reaper
      create  script/process/spawner
      create  script/process/inspector
      create  script/runner
      create  script/server
      create  script/plugin
      create  public/dispatch.rb
      create  public/dispatch.cgi
      create  public/dispatch.fcgi
      create  public/404.html
      create  public/500.html
      create  public/index.html
      create  public/favicon.ico
      create  public/robots.txt
      create  public/images/rails.png
      create  public/javascripts/prototype.js
      create  public/javascripts/effects.js
      create  public/javascripts/dragdrop.js
      create  public/javascripts/controls.js
      create  public/javascripts/application.js
      create  doc/README_FOR_APP
      create  log/server.log
      create  log/production.log
      create  log/development.log
      create  log/test.log
david@sabre:~$ ls
asdf     Documents  Examples               inara.tar    motd.tail  Pictures  repoCheckout  svncgi     test          up.sh   Wallpapers  yeah
Desktop  erp        Firefox_wallpaper.png  jdk1.6.0_02  Music      Public    repos         Templates  transactions  Videos  workspace
david@sabre:~$ cd test
david@sabre:~/test$ ls -lash
total 72K
4.0K drwxr-xr-x 14 david david 4.0K 2008-01-02 20:12 .
4.0K drwxr-xr-x 53 david david 4.0K 2008-01-02 20:12 ..
4.0K drwxr-xr-x  6 david david 4.0K 2008-01-02 20:12 app
4.0K drwxr-xr-x  2 david david 4.0K 2008-01-02 20:12 components
4.0K drwxr-xr-x  3 david david 4.0K 2008-01-02 20:12 config
4.0K drwxr-xr-x  2 david david 4.0K 2008-01-02 20:12 db
4.0K drwxr-xr-x  2 david david 4.0K 2008-01-02 20:12 doc
4.0K drwxr-xr-x  3 david david 4.0K 2008-01-02 20:12 lib
4.0K drwxr-xr-x  2 david david 4.0K 2008-01-02 20:12 log
4.0K drwxr-xr-x  5 david david 4.0K 2008-01-02 20:12 public
4.0K -rw-r--r--  1 david david  307 2008-01-02 20:12 Rakefile
 12K -rw-r--r--  1 david david 8.9K 2008-01-02 20:12 README
4.0K drwxr-xr-x  4 david david 4.0K 2008-01-02 20:12 script
4.0K drwxr-xr-x  7 david david 4.0K 2008-01-02 20:12 test
4.0K drwxr-xr-x  6 david david 4.0K 2008-01-02 20:12 tmp
4.0K drwxr-xr-x  2 david david 4.0K 2008-01-02 20:12 vendor
david@sabre:~/test$ 

```

---

### Post by JESii on 2008-01-03
I believe that I did all the basic stuff that you mentioned... I created the /var/railsapps directory myself -- seemed like a good place to put it since /var/www is often the directory for www files for apache.

I see that you are storing the railsapps in your home directory -- I didn't think I wanted to do that, in case there were other users/user ids on this machine so I wanted the directory in a separate, more public directory.

thanks...jon

---

### Post by JESii on 2008-01-04
Found the problem... and it's a little strange: it was a problem with groups and group recognition.  Here's the deal:

To give user jseidel access to the /var/railsapps directory, I executed:
   adduser jseidel www-data
where www-data is the user/group name associated with the railsapps directory.

However, the output of the groups command was out of synch:
  groups
yielded a list of groups WITHOUT www-data included, whereas
  groups jseidel
yielded a list of groups WITH www-data included.

As soon as I had logged off/on the system, the two commands both included www-data as an authorized group and my rails command worked perfectly.

HTH someone else...jon

---

### Post by JESii on 2008-01-04
Actually, this has already been reported (and confirmed) as a bug: see #162958 on Launchpad.

---

