---
title: "citrix ica client on ubuntu w/ nfuse"
date: 2005-04-12
forum: General Help
---

### Post by haxorwear on 2005-04-12
I've read through the forums and done the following to get my ica client working:

1) Download the 8.x client from Citrix.com for Linux
2) sudo apt-get install libxaw6
3) sudo apt-get install mozilla (just in case firefox didnt work)
4) tar -zxvf linuxx86.tar.gz
5) ./setupwfc and follow prompts to install the client
6) Verify that npica.so is in the plugins directories and check about:plugins in each browser to verify the ica client plugin is in.
7) Tried connecting to our NFUSE published apps portal, logged in, and click on an application link... nothing. I see the citrix window pop up and disappear. 

I also tried downloading the launch.asp file and running /usr/lib/ICAClient/wfica launch.asp and it segmentation faults. I know it segfaulted before installing libxaw6, which is why I did the apt-get install to ensure having those libraries. Any ideas to get past this point?

-Tim

---

### Post by riffic on 2005-04-13
stupid reply, but maybe you could give rdesktop a shot.

---

### Post by haxorwear on 2005-04-13
It was a fair enough suggestion. :)

I don't think rdesktop supports citrix published apps. We have a NFuse published application portal externally at work, which I'd like to use on my Ubuntu laptop. When I have my laptop internally, you can bet that I'd use rdesktop for most of my daily connections to windows remote terminals.

-Tim

---

