---
title: "Installing Revkit"
date: 2013-11-04
forum: General Help
---

### Post by rkverma25 on 2013-11-04
Hi everyone, I am a newbie, so i feel sorry if my questions appear dumb.
I wanted to install revkit from [http://www.informatik.uni-bremen.de/revkit/files/revkit-1.3.tar.gz](http://www.informatik.uni-bremen.de/revkit/files/revkit-1.3.tar.gz)
so i installed ubuntu desktop 13.04 on my laptop
had all the suggested updates and upgrades.
then downloaded the above code
opened the readme file and followed the instructions
first i got error about command git not present. I installed it using synaptic
then i got error about libraries zlib and bzlib...
not sure what to do now....
pls help

---

### Post by 3rdalbum on 2013-11-04
The user manual suggests some commands you should run in order to install all the dependencies: [http://www.informatik.uni-bremen.de/revkit/revkit_user_manual.pdf&#8206;](http://www.informatik.uni-bremen.de/revkit/revkit_user_manual.pdf&#8206;)

However it does say "Ubuntu 9.10 and above" which indicates that this might be very old advice.

If you're getting error messages about missing libraries while compiling, you should install them from Synaptic Package Manager or Apt-get, just remember to install the "-dev" versions. In your case, you probably need "zlib1g-dev" and "libbz2-dev". When you run the compiling stage again it'll probably complain about other libraries that are missing... whenever it does, just keep searching for the libraries you're missing and run the compilation again until it works.

Unfortunately I couldn't find a PPA, repository or Deb package for this Revkit program, so sadly your only option will be to compile it from source. Normally a PPA, repository or Deb package will be a much easier way of installing software.

---

### Post by abhishek-agar2 on 2014-05-17
[COLOR=#000000]i have also been trying to install revkit and i ran the above instruction, however am still getting lots of errors. please can u go through the following question link and the corresponding comments and solve my problem?[/COLOR]
[http://askubuntu.com/questions/46570...install-revkit]("http://askubuntu.com/questions/465703/how-to-install-revkit")

---

