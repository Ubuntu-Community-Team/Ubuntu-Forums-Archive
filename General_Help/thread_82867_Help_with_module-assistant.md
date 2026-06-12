---
title: "Help with module-assistant"
date: 2005-10-27
forum: General Help
---

### Post by Hartigan on 2005-10-27
Hi

I just installed Ubuntu for the very first time, and I have been trying to get Ati-drivers to work. I have tried to follow this guide: [http://ubuntuforums.org/showthread.php?p=423589]("http://ubuntuforums.org/showthread.php?p=423589")

However, when I try to install module-assistant using this line:
```
sudo apt-get install gcc-3.4 module-assistant
```
I get an error, saying the package is not available and has no installationcandidate. Since module-assistant isnt installed logicially I cant get the other steps in the guide to work either.

I am using the 5.10 amd64 version of Ubuntu. Any help will be appreciated.

---

### Post by oskude on 2005-11-03
hi,

i had the same problem and google gave me this thread as the first answer to "ubuntu module-assistant", so i had to post the/a solution :) 

you have to add the "universe" repository for apt, to do this open the sources.list file:```
sudo nano /etc/apt/sources.list
```UNcomment the following lines:```
# deb http://your.url.to.ubuntu.com/ubuntu/ breezy universe
# deb-src http://your.url.to.ubuntu.com/ubuntu/ breezy universe
```now a quick update:```
sudo apt-get update
```and now "module-assistant" will be found

cheers
osku[de]

---

