---
title: "Install F-Spot-0.3.5 in Dapper?"
date: 2007-06-05
forum: General Help
---

### Post by ubuntubrian on 2007-06-05
Is it possible to build the latest version of F-Spot (0.3.5) and install it on Dapper?
The 0.1.1 version crashes a lot and I'm hoping that the newer version is more stable.
Thanks

---

### Post by steeleyuk on 2007-06-05
Instructions from the F-spot site [here]("http://f-spot.org/How_To_Build_from_Release"). As long as you get the necessary dependencies you shouldn't have any problems.

---

### Post by ubuntubrian on 2007-06-05
I also found a .deb package for ppc which would be easy to install also, maybe. I may just install it from source into my home directory and run it non-system wide as I have done for Firefox-2.0. any additional advice is most welcome.
Thanks for the reply

---

### Post by ubuntubrian on 2007-06-05
OK. Dapper doesn't have most of the dependencies in latest versions. Can you suggest the best way to download and install them? 
Thanks

---

### Post by steeleyuk on 2007-06-05
Try running in the terminal:

sudo apt-get build-dep f-spot

Then try building from source.

---

### Post by ubuntubrian on 2007-06-05
Yeah, I tried that too but apt-get only shows the dependencies as the latest available and so the build fails with most of the dependencies not met. For example mono is 1.1.3 and I need 1.1.7, not available with Dapper. I hesitate to start looking for debs and just installing them. I guess newer versions aren't backported to Dapper and in looking at the Launchpad page for F-Spot it shows specific F-Spot versions for certain Ubuntu versions. 0.3.5 is available for Feisty and 0.1.1 for Dapper. Can I upgrade the dependencies?
Thanks

---

### Post by ubuntubrian on 2007-06-05
So this is why- the reply is #18 above #17 below it. Seems too difficult at this time. this is from the thread:
[http://ubuntuforums.org/showthread.php?t=268687&page=18](http://ubuntuforums.org/showthread.php?t=268687&page=18)

"#18   Report Post  
Old October 1st, 2006
jdong's Avatar 	
jdong jdong is offline
Ultimate Coffee Grinder
	  	
Join Date: Oct 2004
Location: Cambridge. MA
Beans: 5,815
The Feisty Fawn Testing User
Re: Build (backport) an Edgy package to run on Dapper
1) I would advise against mono backports, unless you intend on backporting all of mono (which would work). The mono packaging style completely changed from dapper to edgy to more match Debian's packaging, rendering the two incompatible.

2) You need to run sudo prevu-update after your cli-common-dev compile for prevu to realize the new package exists. Installing it on your system does no good, because prevu builds its packages in an isolated, clean environment.
__________________
From local newspaper:
Quote:
If you find yourself being chased by a dog while walking, jogging or bicycling, stop, turn toward dog, point, and firmly say "No!" or "Go home!". Repeat as needed.
This is effective even for dogs that do not speak English
Reply With Quote Multi-Quote This Message Quick reply to this message
jdong
View Public Profile
Send a private message to jdong
Send email to jdong
Visit jdong's homepage!
Find all posts by jdong
Add jdong to Your Buddy List
  #17   Report Post  
Old October 1st, 2006
foxy123 foxy123 is offline
Fresh Brewed Ubuntu
	  	
Join Date: Apr 2005
Beans: 1,251
Re: Build (backport) an Edgy package to run on Dapper
OK I am trying to build a new f-spot and ran into cli-comon-dev dependancy. I built cli-common-dev from Edgy souce and installed it:
Code:

:~$ apt-cache showpkg cli-common-dev
Package: cli-common-dev
Versions:
0.4.3ubuntu1~6.06prevu1(/var/lib/dpkg/status)

But f-spot still complains about dependency:

Code:

 -> Considering  cli-common-dev (>= 0.2.0)
W: Unable to locate package cli-common-dev
E: No packages found
      Tried versions:
   -> Does not satisfy version, not trying
E: Could not satisfy build-dependency.
E: pbuilder-satisfydepends failed."

---

### Post by suoko on 2007-08-22
f-spot 0.35 is really needed for dapper since previous versions do not work with picasa, then it's useless.

---

