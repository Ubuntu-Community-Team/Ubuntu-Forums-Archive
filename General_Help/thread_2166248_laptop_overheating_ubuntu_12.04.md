---
title: "laptop overheating ubuntu 12.04"
date: 2013-08-08
forum: General Help
---

### Post by arhs_faust on 2013-08-08
Hello. I am new in Ubuntu and i am having big overheating problems with cpu and graphic card which i would like to solve if possible.
i am running 12.04 lts with 3.5.0-37-generic kernel. 
my laptop features are: 
Intel  Core 2 Duo CPU T5800 @ 2.00GHz × 2 
3.0 GiB ram and nvidia geforce graphic card.
Thanks in advance!

---

### Post by Mark Phelps on 2013-08-08
We used to recommend installing Jupiter to address the overheating -- but Jupiter has been abandoned.

So now, you should try tlp instead:

> sudo add-apt-repository ppa:linrunner/tlp
sudo apt-get update
sudo apt-get install tlp tlp-rdw

> sudo tlp start

---

### Post by arhs_faust on 2013-08-08
I allready have jupiter installed but it seems not to help.... Should i remove jupiter and install the package u subscribed?

---

### Post by Netstatus on 2013-08-08
You might as well do so. Tlp works well for my netbook.

---

### Post by arhs_faust on 2013-08-09
i installed tlp but it doesnt seem to help much. I am just surfing to internet and heat rises to 70 C for both prossesor and graphic card...

---

### Post by Netstatus on 2013-08-09
Are you sure that there is not simply something wrong on the hardware side of things?

Is the fan working correctly?
Might dust have gathered within the laptop? (Thus rendering rendering the fan ineffective)

---

### Post by SweetAurora on 2013-08-09
Did you install the graphics driver? Is this a hybrid system?

---

### Post by arhs_faust on 2013-08-09
Problem is solved. It was hardware's fault... i just blew it with comressed air and now is working as cold as ice.... 58 C max temperature....Thank u all for your time! ^_-

---

### Post by Netstatus on 2013-08-09
That's what I had guessed. I suggest you do so once in a while.
Please don't forget to mark the thread as solved once you're content with it.

---

