---
title: "Server w/GUI vs Desktop Edition"
date: 2007-12-11
forum: General Help
---

### Post by rsw686 on 2007-12-11
Are there any difference in the kernels between the server and desktop editions? Basically what I'm trying to determine is if the server version is optimized for servers besides just removing all the extras. 

I'm looking to install VMWare on Ubuntu. I don't need the GUI, but it would come in handy as I could manage the virtual machines at the box instead of having to connect remotely.

If I install Ubuntu Server edition and add the GUI with apt-get or if I install the Ubuntu Desktop edition I should be getting the same thing or not?

Which would be the preferred method? I'm assuming if I go with the server install then add the gui it will come to a command line login and then I start the GUI as needed with startx?

---

### Post by bodhi.zazen on 2007-12-11
Yes, the server edition comes with a different kernel.

Why do you want a gui ? just to run VMWare ?

From what you are describing I would take a look at OpenVZ

---

