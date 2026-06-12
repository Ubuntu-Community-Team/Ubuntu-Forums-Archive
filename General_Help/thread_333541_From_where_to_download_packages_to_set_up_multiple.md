---
title: "From where to download packages to set up multiple computers with fresh install"
date: 2007-01-07
forum: General Help
---

### Post by puneit on 2007-01-07
I live in a campus and I want to infect everyone around me with the Linux bug. I have impressed a couple of my friends till now and 3 have already installed Ubuntu Edgy and are very happy with it. 
I want that along with the installation media that I willingly distribute to my friends, I should also be able to distribute pre-downloaded packages like audio/video codecs, samba, smbfs, flash etc. That is everything, that, makes Ubuntu complete. Though I use and recommend Automatix for same, but then not always the download speeds are fast. And since we live in a campus, many a times, the network chokes. 
And I don't wish to make them feel frustrated, if for some reason they are not able to play their mp3s.
So, someone please guide me on how to do this.

---

### Post by meng on 2007-01-07
If you want flash and audio/video codecs, you're probably best to get Linux Mint (based on Ubuntu) or PCLinuxOS.

---

### Post by puneit on 2007-01-07
I was looking for common repository link or something :) and not a suggestion to try out another distro
Ubuntu based is not Ubuntu

---

### Post by koenn on 2007-01-07
1-
as the repo's are essentially webservers, any caching proxy server would help to reduce the download times (i.e. if you set up a server with squid, you 'd all be downloading from that server). 

2-
there used to be apt-proxy, which works as a proxy server but optimized for downloading and caching packages. I used it with Debian, but i believe Ubuntu also has it. 
It's better than a normal caching proxy (like squid) because it can handle large volumes (lots of packages,  ususally bigger than the average web page) better

3-
Then, of course, you could just download a (seletion from) the packages on the ubuntu archive servers, and set up a small archive server for you and your friends.
You'd need a web server (apache) and some scripts to create Package.gz and Release.gz files, and ideally reproduce the main - restricted - universe - multiverse directory structure. 

Debian has scripts and documentation that explain how to do that, and most of it will apply to Ubuntu, but if you're new to Linux (and networking), it might be a bit challenging.

---

### Post by meng on 2007-01-07
> **puneit said:**
> I was looking for common repository link or something :) and not a suggestion to try out another distro
Ubuntu based is not Ubuntu
Thanks for clarifying what you want. I made the suggestion because I felt it was easier to try out something similar than to remaster your own CD, which is essentially what you are asking to do. (Indeed, you would probably need to make it a DVD unless you removed some default applications.) If you do a search for remaster Ubuntu you may find what you are looking for.

---

