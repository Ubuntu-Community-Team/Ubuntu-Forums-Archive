---
title: "apt-get problem"
date: 2008-06-10
forum: General Help
---

### Post by AllanDu on 2008-06-10
Hi,

I installed rails and ruby on my desktop days before, and now no matter I try apt-get install anything will give me the error massage like below
sudo apt-get install php4-curl

Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  php4-curl: Depends: phpapi-20050606
  ruby-gems-gem-plugin: Depends: ruby-gems-rake (>= 0.7) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

And if I try sudo apt-get -f install will get 

sudo apt-get -f install          

Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  ruby-gems-rake
The following NEW packages will be installed:
  ruby-gems-rake
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B/249kB of archives.
After unpacking 1655kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
WARNING: The following packages cannot be authenticated!
  ruby-gems-rake
Install these packages without verification [y/N]? y
(Reading database ... 279356 files and directories currently installed.)
Unpacking ruby-gems-rake (from .../ruby-gems-rake_0.7.2_all.deb) ...
dpkg: error processing /var/cache/apt/archives/ruby-gems-rake_0.7.2_all.deb (--unpack):
 trying to overwrite `/usr/bin/rake', which is also in package rake
Errors were encountered while processing:
 /var/cache/apt/archives/ruby-gems-rake_0.7.2_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

What should I do?
Thanks

---

### Post by VMC on 2008-06-10
> **AllanDu said:**
> Hi,

I installed rails and ruby on my desktop days before, and now no matter I try apt-get install anything will give me the error massage like below
sudo apt-get install php4-curl

Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  php4-curl: Depends: phpapi-20050606
  ruby-gems-gem-plugin: Depends: ruby-gems-rake (>= 0.7) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

And if I try sudo apt-get -f install will get 

sudo apt-get -f install          

Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  ruby-gems-rake
The following NEW packages will be installed:
  ruby-gems-rake
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B/249kB of archives.
After unpacking 1655kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
WARNING: The following packages cannot be authenticated!
  ruby-gems-rake
Install these packages without verification [y/N]? y
(Reading database ... 279356 files and directories currently installed.)
Unpacking ruby-gems-rake (from .../ruby-gems-rake_0.7.2_all.deb) ...
dpkg: error processing /var/cache/apt/archives/ruby-gems-rake_0.7.2_all.deb (--unpack):
 trying to overwrite `/usr/bin/rake', which is also in package rake
Errors were encountered while processing:
 /var/cache/apt/archives/ruby-gems-rake_0.7.2_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

What should I do?
Thanks

Does "sudo apt-get purge" show anything?

---

### Post by brian_p on 2008-06-10
> **AllanDu said:**
> 
(Reading database ... 279356 files and directories currently installed.)
Unpacking ruby-gems-rake (from .../ruby-gems-rake_0.7.2_all.deb) ...
dpkg: error processing /var/cache/apt/archives/ruby-gems-rake_0.7.2_all.deb (--unpack):
 trying to overwrite `/usr/bin/rake', which is also in package rake
Errors were encountered while processing:
 /var/cache/apt/archives/ruby-gems-rake_0.7.2_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

What should I do?
Thanks

You have the distinction that your post is the only entry given by a Google search for ruby-gems-rake_0.7.2_all.deb. Where did you get it from?

---

