---
title: "Apache2 configured with php as cgi module"
date: 2007-10-07
forum: General Help
---

### Post by elijathegold on 2007-10-07
I have a server that has been set up by a predecessor. 

This server is running Ubuntu 6.06 LTS Server with Apache2 and php5 installed (according to phpinfo)
as a fast-cgi module. There will be a site going live on this server fairly soon that we expect to 
generate a huge amount of traffic, so much so that this site and a couple of its sub sites will be
all it is running!

I'm a relative beginner with Linux in general, but I understand that it is better to install php5 as an
Apache2 module rather than a cgi module. I can easily install the required module using apt-get
and a2enmod but I am unsure if I can just do this when it is already using the cgi version.

Is there anything else I will need to do?

I am also going to turn of keep-alives and increase the number of instances started up

I have root access through ssh and this whole thing is run using command line only.

---

