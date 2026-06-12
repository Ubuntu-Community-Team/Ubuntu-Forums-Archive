---
title: "Libre Office 5 vs. 6 -- where did it go?"
date: 2018-06-11
forum: General Help
---

### Post by edstevens on 2018-06-11
Running ubuntu 16.04 LTS
Running Cinnamon desktop.
Have had Libre Office 5 installed from "the beginning".  Use it quite a bit for word processing and spreadsheets.  Yesterday I needed to throw together a little database so went to open 'data' and get started.  From my Cinnamon 'start' menu, I selected "office", which opened a sub-menu containing the following
- LibreOffice
- LibreOffice Calc
- LibreOffice Draw
- LibreOffice Impress
- LibreOffice Math
- LibreOffice Writer

But no "Data"
If I opened the generic - LibreOffice, it gave a navigation pane to "create new", with an option for database, but clicking on it did nothing.

So I decided to try downloading the latest LO.  Did so and launched at end of download.  Threw together a litttle database.  Save it and closed out.  Came back today, my "start menu" button gives the same options as yesterday.  Nothing to open LibreOffice Data.  I had to open a shell prompt and do a manual 'find / -name "*.odt" to locate my db file. Once located, I was able to open it by going back to Nemo, drilling down to the file and double clicking it. It was then that I noticed it was opening with LO 6.

Also, I notice that If I open anything with LO5 and select to open 'recent' files, only the files that had been opened with LO 5 are listed.  If I go back to Nemo and drill down to one of those files and simply select "open" it opens with LO 5.  But I can select "open WITH" and get the option to open LO 6.

So I guess the question is, how do I _replace_ LO 5 with 6, and get 6 into my "start menu".

---

### Post by deadflowr on 2018-06-11
Easiest way is to use the libreoffice ppa
[https://launchpad.net/~libreoffice/+archive/ubuntu/ppa]("https://launchpad.net/~libreoffice/+archive/ubuntu/ppa")

Note that the database package is libreoffice-base.
Not to be confused with libreoffice-base-core.
ftr

---

### Post by edstevens on 2018-06-11
@Deadflowr
Hmm.  Not sure see how to do that .. how to actually install it ...
Not to mention this rather disconcerting statement from the page you linked:  "unsupported packages from           this untrusted PPA"

---

### Post by monkeybrain20122 on 2018-06-11
> **edstevens said:**
> @Deadflowr
Hmm.  Not sure see how to do that .. how to actually install it ...
Not to mention this rather disconcerting statement from the page you linked:  "unsupported packages from           this untrusted PPA"

The page provides instruction to install
```

sudo add-apt-repository ppa:libreoffice/ppa

sudo apt update

sudo apt upgrade
```

Don't mind the statement, it is a standard disclaimer, just means that it is not an "official" canonical repository.

---

### Post by edstevens on 2018-06-12
@monkeybrain20122 -- sorry, but even going back and looking specifically, I don't see those commands on the page linked by deadflowr. However, I took the commands you provided and I now have LO 6 fully functional and listed/linked from my 'start menu'.  Thank you for the assistance.

  FWIW, software installation in Debian-based linux's is still pretty new to me.  I'm much more familiar with  using 'yum' in RedHat based linux.

---

### Post by monkeybrain20122 on 2018-06-16
> **edstevens said:**
> @monkeybrain20122 -- sorry, but even going back and looking specifically, I don't see those commands on the page linked by deadflowr. However, I took the commands you provided and I now have LO 6 fully functional and listed/linked from my 'start menu'.  Thank you for the assistance..

The info is in the section "Adding this ppa to your system" in the middle of the page

> 
  FWIW, software installation in Debian-based linux's is still pretty new to me.  I'm much more familiar with  using 'yum' in RedHat based linux.

Fedora no longer uses yum, switched to dnf a few releases ago.:P

---

