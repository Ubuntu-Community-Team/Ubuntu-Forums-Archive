---
title: "problem installing ruby1.8-dev"
date: 2006-08-23
forum: General Help
---

### Post by JediAnt on 2006-08-23
Hi there. I need to install Ruby with the ruby1.8-dev package in order to use it to extconf another package. Ruby installs fine, but the dev package fails. It seems to depend on itself?? Here is the console output..
[Thanks in advance]

jediant@jediant-lap0:~/ruby/ruby-xslt$ sudo apt-get install ruby
Password:
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  ruby1.8
Suggested packages:
  ruby1.8-examples rdoc1.8 ri1.8
The following NEW packages will be installed:
  ruby ruby1.8
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 207kB of archives.
After unpacking 373kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main ruby1.8 1.8.4-1ubuntu1 [188kB]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main ruby 1.8.2-1 [19.0kB]
Fetched 207kB in 43s (4730B/s)
Selecting previously deselected package ruby1.8.
(Reading database ... 93246 files and directories currently installed.)
Unpacking ruby1.8 (from .../ruby1.8_1.8.4-1ubuntu1_i386.deb) ...
Selecting previously deselected package ruby.
Unpacking ruby (from .../archives/ruby_1.8.2-1_all.deb) ...
Setting up ruby1.8 (1.8.4-1ubuntu1) ...
Setting up ruby (1.8.2-1) ...
jediant@jediant-lap0:~/ruby/ruby-xslt$ sudo apt-get install ruby1.8-dev
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  ruby1.8-dev: Depends: libruby1.8 (= 1.8.4-1ubuntu1) but 1.8.4-1ubuntu1.1 is to be installed
E: Broken packages

---

