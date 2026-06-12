---
title: "Installing Ruby on EC2"
date: 2014-08-06
forum: General Help
---

### Post by mike223 on 2014-08-06
I'm trying to install ruby on an EC2 instance running ubuntu 12.1.  This is what I get.  Can anyone help me?

ubuntu@ip-10-0-1-14:/etc/apt$ sudo apt-get install ruby
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  libruby1.9.1 ruby1.9.1
Suggested packages:
  ri ruby-dev ruby1.9.1-examples ri1.9.1 graphviz ruby1.9.1-dev ruby-switch
The following NEW packages will be installed:
  libruby1.9.1 ruby ruby1.9.1
0 upgraded, 3 newly installed, 0 to remove and 33 not upgraded.
Need to get 4,149 kB of archives.
After this operation, 12.6 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Err [http://us-west-2.ec2.archive.ubuntu.com/ubuntu/](http://us-west-2.ec2.archive.ubuntu.com/ubuntu/) quantal-updates/main libruby1.9.1 amd64 1.9.3.194-1ubuntu1.6
  403  Forbidden
Err [http://us-west-2.ec2.archive.ubuntu.com/ubuntu/](http://us-west-2.ec2.archive.ubuntu.com/ubuntu/) quantal-updates/main ruby1.9.1 amd64 1.9.3.194-1ubuntu1.6
  403  Forbidden
Err [http://us-west-2.ec2.archive.ubuntu.com/ubuntu/](http://us-west-2.ec2.archive.ubuntu.com/ubuntu/) quantal/main ruby all 4.9
  403  Forbidden
Failed to fetch [http://us-west-2.ec2.archive.ubuntu.com/ubuntu/pool/main/r/ruby1.9.1/libruby1.9.1_1.9.3.194-1ubuntu1.6_amd64.deb](http://us-west-2.ec2.archive.ubuntu.com/ubuntu/pool/main/r/ruby1.9.1/libruby1.9.1_1.9.3.194-1ubuntu1.6_amd64.deb)  403  Forbidden
Failed to fetch [http://us-west-2.ec2.archive.ubuntu.com/ubuntu/pool/main/r/ruby1.9.1/ruby1.9.1_1.9.3.194-1ubuntu1.6_amd64.deb](http://us-west-2.ec2.archive.ubuntu.com/ubuntu/pool/main/r/ruby1.9.1/ruby1.9.1_1.9.3.194-1ubuntu1.6_amd64.deb)  403  Forbidden
Failed to fetch [http://us-west-2.ec2.archive.ubuntu.com/ubuntu/pool/main/r/ruby-defaults/ruby_4.9_all.deb](http://us-west-2.ec2.archive.ubuntu.com/ubuntu/pool/main/r/ruby-defaults/ruby_4.9_all.deb)  403  Forbidden
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
ubuntu@ip-10-0-1-14:/etc/apt$

I did read on another forum that the AWS libraries can only be accessed if you subscribe to them.  That post suggested changing us-west-2.ec2.archive.ubuntu.com/ubuntu/ with just archive.ubuntu.com/ubuntu.  When I tried that, I get...
ubuntu@ip-10-0-1-14:/etc/apt$ sudo apt-get install ruby
Reading package lists... Done
Building dependency tree
Reading state information... Done
Note, selecting 'ruby1.8' instead of 'ruby'
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 ruby1.8 : Depends: libruby1.8 (= 1.8.7.358-4ubuntu0.4) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

So I try installing libruby1.8, and I get...
ubuntu@ip-10-0-1-14:/etc/apt$ sudo apt-get install libruby1.8
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 libruby1.8 : Depends: libreadline5 (>= 5.2) but it is not installable
E: Unable to correct problems, you have held broken packages.

So, I try to install libreadline5, and I get...
ubuntu@ip-10-0-1-14:/etc/apt$ sudo apt-get install libreadlines5
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Unable to locate package libreadlines5
ubuntu@ip-10-0-1-14:/etc/apt$

Now what?

Any help greatly appreciated.

Thanks.

---

### Post by mike223 on 2014-08-06
Seems to have been a problem with the AMI that I used.  I used one from the community that for some reason didn't register my EC2 instance with AWS' services.  I built another instance based on an AMI from the Market Place (with $0 subscription), and it worked fine.

---

