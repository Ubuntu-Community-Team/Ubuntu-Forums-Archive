---
title: "problems adding a new screensaver"
date: 2016-12-01
forum: General Help
---

### Post by Graham_Mitchell on 2016-12-01
I recently saw this article - [http://www.omgubuntu.co.uk/2016/11/gluqlo-flipqlo-screensaver-ubuntu](http://www.omgubuntu.co.uk/2016/11/gluqlo-flipqlo-screensaver-ubuntu) and thought I'd give it a go. As a noob little things like this are useful to help develop my understanding. I followed the instructions to install xscreensaver on my clean Ubuntu 16.04 system, and then to install the Gluqlo flip clock.

As the article mentioned, Gluqlo was not visible in my Screensaver preferences so, again as instructed, I edited the ~/.xscreensaver file to include the reference to gluqlo.

Quit the screensaver preferences, relaunch - and nothing had changed. Looking again the ~/.xscreensaver file I could see that edit had been overwritten. What appears to be happening is that xscreensaver is overwriting my preferences file every time it starts up, making it impossible for me to add the Gluqlo display.

Any thoughts as to how to solve this most welcome.

Thanks
Graham

---

### Post by Graham_Mitchell on 2016-12-01
The instructions given suggest that to add the Gluqlo clock to the list of available screensavers in xscreensaver-demo the file at ~/.xscreensaver should have the line 
gluqlo -root  \n\ appended in the 'products' section.
Removing the -root option solved the problem.

---

