---
title: "error starting up Libre Office"
date: 2020-03-11
forum: General Help
---

### Post by Skaperen on 2020-03-11
i try to start Libre Office graphically with background > Applications > Office > LibreOffice (in Xfce under Xubuntu) and it always fails before even a splash window, showing [this error message]("http://ipal.net/u/2020031019-error-message.png").  i had not specified a filename, so it must be trying to open an application or system file.  anyone know what this means and/or the file it is trying to open and/or the meaning of the given context?

---

### Post by SeijiSensei on 2020-03-12
I see you're running 6.0.  Maybe you should try 6.3 from 

[https://launchpad.net/~libreoffice/+archive/ubuntu/libreoffice-6-3](https://launchpad.net/~libreoffice/+archive/ubuntu/libreoffice-6-3)

or 6.4 from 

[https://launchpad.net/~libreoffice/+archive/ubuntu/libreoffice-prereleases](https://launchpad.net/~libreoffice/+archive/ubuntu/libreoffice-prereleases)

I'm running Kubuntu 20.04 which comes with 6.4.  Haven't had any issues.

Also this thread is tagged with [Kubuntu].  Shouldn't it be [Xubuntu]?

---

### Post by Skaperen on 2020-03-12
if 6.0 is broken, maybe Canonical should make the change.  i do keep my 18.04 LTS Xubuntu upgraded.  how can you tell it's 6.0?

---

### Post by SeijiSensei on 2020-03-13
It's displayed in the bar in the image you posted.

---

### Post by Skaperen on 2020-03-13
indeed it is.  that text is too small for me to read (xmag to the rescue).

what version are you or others running?

---

### Post by SeijiSensei on 2020-03-13
On this machine running the advance release of Kubuntu 20.04, I have LibreOffice 6.4.0.3. That came along with the installation.  I think my 19.04 and 19.10 installations include 6.3.

---

### Post by ajgreeny on 2020-03-13
I am using:-
> Version: 6.3.5.2
Build ID: 1:6.3.5~rc2-0ubuntu0.18.04.1~lo1
Which comes from the LibreOffice-ppa at [https://launchpad.net/~libreoffice/+archive/ubuntu/ppa](https://launchpad.net/~libreoffice/+archive/ubuntu/ppa)

I've been using this very trustworthy ppa for a few years now and it has been absolutely fine in both Xubuntu 16.04 and 18.04.

I do wonder, however, if you might get it running simply by closing all LO apps then renaming the configuration folder at ~/.config/libreoffice as ~/.config/libreoffice-backup and restarting LO.

---

### Post by Skaperen on 2020-03-13
> **ajgreeny said:**
> I do wonder, however, if you might get it running simply by closing all LO apps then renaming the configuration folder at ~/.config/libreoffice as ~/.config/libreoffice-backup and restarting LO.

would i have to have 6.3 already installed to do that?

---

### Post by Skaperen on 2020-03-13
it looks like i accidentally marked this thread as kubuntu.  how can i change that marking?  it should be xubuntu.

---

### Post by wildmanne39 on 2020-03-13
> 

    it looks like i accidentally marked this thread as kubuntu. how can i change that marking? it should be xubuntu. 


I changed it for you.

---

### Post by mörgæs on 2020-03-14
> **Skaperen said:**
> if 6.0 is broken, maybe Canonical should make the change.
They did, and a bugfixed version of Libreoffice is available in 19.10. 
LTS means stable which is the opposite of improvement. In a LTS security related bugs are fixed but bugs related to function are normally not. I refer to LTS as a museum for old bugs.


> **Skaperen said:**
> I do keep my 18.04 LTS Xubuntu upgraded.
That keeps you safe from security breaches which of course is top priority. However, if an old release like 18.04 does not function the way you want then there is no point in keeping it. 

In some cases PPA's solve the problem (and they appear to in this case) but their quality can vary.

---

### Post by Skaperen on 2020-03-14
> **wildmanne39 said:**
> I changed it for you.

than you!

---

### Post by Skaperen on 2020-03-14
but versions like 19.10 require too frequent total upgrade.  there is nothing in between.

---

### Post by ajgreeny on 2020-03-14
> **Skaperen said:**
> but versions like 19.10 require too frequent total upgrade.  there is nothing in between.
Which is partly why the PPA system is available; it allows you to add an updated version of certain applications, which I admit you must make up your own mind about the trust you put in that specific PPA.

Some PPAs are kept updated by the application developers, in this case LibreOffice itself, and it has, as I said, been faultless for me.

Have you tried the configuration renaming suggestion I gave in my last post?  Did it have ant effect?

---

### Post by mörgæs on 2020-03-17
> **Skaperen said:**
> but versions like 19.10 require too frequent total upgrade.  there is nothing in between.

It requires one reinstall today and another in july when support for 19.10 runs out. If you don't experience bugs in 20.04 you can keep it in three / five years.

---

### Post by him610 on 2020-03-17
Xubuntu 20.04 LibreOffice Version: 6.4.0.3

If there be tested updates before LTS 20.04.1, most likely will be included. 
I also get periodic updates from the LibreOffice folks advising me of updates. You should get on their emailing list.

---

### Post by deadflowr on 2020-03-17
Have you tried nuking the libreoffice user profile first?
(libreoffice user settings are located at ~/.config/libreoffice)
there is nothing this significantly broken about libreoffice 6.0 on Ubuntu 18.04,
the issue is far more likely an end user issue here.

Alternatively you can try either the snap version (currently at 6.4.1.2)
or flatpak has it packaged, same updated version as the snap version.

So, along with the PPA there really is no reason to wipe the system to reinstall a (at this point in time) a very short term release like 19.10.

---

### Post by Skaperen on 2020-03-18
what about backports?

---

### Post by mörgæs on 2020-03-19
A lot of advice has been given. I think it's time for you to begin experimenting.

---

### Post by him610 on 2020-03-19
From an email I received today from the Document Foundation:
> Berlin, March 19, 2020 &#8211; The Document Foundation announces the availability of LibreOffice 6.4.2, the 2nd minor release of the LibreOffice 6.4 family, targeted at technology enthusiasts and power users. LibreOffice 6.4.2 includes several bug fixes and improvements to document compatibility.

---

### Post by Skaperen on 2020-03-19
i certainly don't want to be experimenting with something that could break the only system i have (which is why i worry even when i do [COLOR=#0000cd][FONT=courier new]**apt-get upgrade**[/FONT][/COLOR], which has messed things up only once).  i script what works.

---

