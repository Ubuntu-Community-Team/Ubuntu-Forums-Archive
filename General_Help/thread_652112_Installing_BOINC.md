---
title: "Installing BOINC"
date: 2007-12-28
forum: General Help
---

### Post by jcfisher on 2007-12-28
I've been trying to install BOINC, Berkeley's distributed computing infrastructure (formerly SETI@home).  Installation -
```
$ sudo apt-get install boinc-client boinc-manager
```
- runs successfully, but afterwards the BOINC manager tells me that I'm running it in the wrong directory.

Here's what I'd like it to do.  I'd like it to run automatically at startup (which it seems to do anyway), and I'd like to be able to manage it using the GUI, boincmgr.  I know a number of people have written about this topic, but none of their instructions have worked for me, so if someone could help walk me through this, I'd be very grateful.

Jake

---

### Post by Niniel on 2008-01-06
I just want to know how to attach my project... I want to do SETI work, but now that I have BOINC, I am stuck. 
Has anybody done this before and can give advice?

Thank you.

---

### Post by oldos2er on 2008-01-06
jcfisher, check under the Applications, Accessories menu, and see if you can start boinc manager graphically. If you don't have boinc client running, it'll probably complain about that.

 Niniel, if you already have a SETI project account, open boinc manager and choose 'Add Project.'

---

### Post by jcfisher on 2008-01-11
Ann,

Thanks for your help.  I am embarrassed to say that almost immediately after I posted that, I rebooted, then typed "localhost" under the "Select computer" section of boincmgr, a fix which has been suggested many times.  However, if you know of a way to fix boincmgr such that I don't have to enter "localhost" every time I want to run it, I would love to hear about it.

Jake

---

### Post by oldos2er on 2008-01-11
No, I'm afraid I don't. Hopefully someone who knows will post.

---

### Post by Niniel on 2008-01-12
It won't connect to localhost for me. Anything I need to configure somewhere else?

---

### Post by StrawberryAngel on 2008-02-06
> **jcfisher said:**
> I've been trying to install BOINC, Berkeley's distributed computing infrastructure (formerly SETI@home).  Installation -
```
$ sudo apt-get install boinc-client boinc-manager
```
- runs successfully, but afterwards the BOINC manager tells me that I'm running it in the wrong directory.

Here's what I'd like it to do.  I'd like it to run automatically at startup (which it seems to do anyway), and I'd like to be able to manage it using the GUI, boincmgr.  I know a number of people have written about this topic, but none of their instructions have worked for me, so if someone could help walk me through this, I'd be very grateful.

Jake

Thank you.  I used  sudo apt-get install boinc-client boinc-manage to get Boinc working for me in Ubuntu 7.10 and its performing just fine. 

                                                                          Stephanie

---

