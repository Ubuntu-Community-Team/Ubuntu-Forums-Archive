---
title: "gOS on Cloudbook"
date: 2008-02-27
forum: General Help
---

### Post by sbphoto on 2008-02-27
Hello, everyone. I am new here. Comments and/or help will be much appreciated about making the Everex Cloudbook I received a few days ago more functional.

1) The mouse tends to freeze so I've had problems after the prolonged start-up requiring total system shutdown (pulling the battery) and re-boot. There must be a better way but keyboard and mouse/pointer functions are frozen so I did not see another way.

2) Things are not correctly sized for the screen so required input commands may be off screen and there is no obvious scrolling mechanism (last experienced when trying to use Open Office Base).

3) I don't like the Google Toolbar junk which takes up room at the bottom of the screen (and perhaps CPU time as well) so I am tempted to dump gOS completely and load Debian or Ubuntu....BUT...I have not tried to boot from a live CD via an external CD ROM and don't know what I'd be getting into. Has anyone else replaced gOS with something faster and more solid on a Cloudbook?

Looking forward to your comments.

---

### Post by danramos on 2008-02-29
I'm not sure what the deal is with your mouse freezing problem.  I've not run into that.. but on my Cloudbook, I also found the Google toolbar pre-installed, annoyingly.  You can remove it by going to APPLICATIONS -> ACCESSORIES -> TERMINAL and issuing this command:

sudo apt-get remove firefox-google-toolbar-plugin

Hope that helps at least the one problem.  For your other problem, leave your terminal open and after the mouse locks up, issue a 'dmesg' and see if it reports any specific errors having to do with the mouse hardware.

---

### Post by danramos on 2008-02-29
Sorry, I also forgot to address your oversized window problem.  You can get around the problem by holding the ALT key while you drag the window.  That'll at least make it so that you can move along and productively get past any dialog box.

---

### Post by /home on 2008-02-29
Remove all the google crap and Gos rocks!

---

### Post by sbphoto on 2008-03-13
Thanks for the suggestions, folks. I will try them when I get a restoration gOS. In trying to fix the OS problems I was having, my gOS became FUBAR. So, for now, my Cloudbook is serving as a paperweight. It is a nice looking paperweight...and...as a paperweight, there is no delay upon start-up for this function. I'll let everyone know how things go when/if I get a working OS from Everex or from the gOS site.

I will put up with this to rid myself of as much Microsoft as possible. If I were not on that quest, this sort of software + customer support problem would really upset me.

---

