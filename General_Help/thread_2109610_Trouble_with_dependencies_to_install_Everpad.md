---
title: "Trouble with dependencies to install Everpad"
date: 2013-01-28
forum: General Help
---

### Post by arrrimapirate on 2013-01-28
I'm trying to install everpad for Ubuntu 12.10 64 bit.
*If the problem is because I'm using 64-bit then don't bother to read the  rest. Though I don't see anything for 64-bit. If this is the issue  please direct me and I'll put on the dunce cap.*

I added the ppa with the following:

```
sudo add-apt-repository ppa:nvbn-rm/ppa
sudo apt-get update && sudo apt-get install everpad
```Terminal returned the following

```
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 everpad : Depends: python-magic but it is not going to be installed
           Depends: gtk2-engines-pixbuf but it is not going to be installed
```I tried installing using -f and it returned the same. 
Tried installing python-magic in synaptic, but that says I need libmagic1 (=5.11-1)
I have libmagic 5.11-2

ftk2-engines-pixbuf in Synaptic says depends is libgtk2.0-0 (=2.24.10-0ubuntu6)

Any ideas? I often have bad luck with PPAs. I really like everpad and I would like to be able to access my notes from my desktop computer natively.

---

### Post by stinkeye on 2013-01-28
FYI it installs here on Ubuntu 12.10 64 bit.
> The following NEW packages will be installed:
  everpad libpyside1.1 libshiboken1.1 python-beautifulsoup python-html2text python-magic python-oauth2 python-pyside.qtcore python-pyside.qtgui
  python-pyside.qtnetwork python-pyside.qtwebkit python-pysqlite2 python-regex python-sqlalchemy python-sqlalchemy-ext python-unity-singlet
My current version of gtk2-engines-pixbuf is **2.24.13-0ubuntu2**
and Depends:libgtk2.0-0(=**2.24.13-0ubuntu2**).
Does your installed version for **gtk2-engines-pixbuf** match the latest version shown in synaptic?.
If not, do you have the universe repo enabled in software sources?
Maybe just need to run an upgrade first.
[ATTACH]230745[/ATTACH]  [ATTACH]230747[/ATTACH]

or
Do you have other added ppa's.
May be packages from those ppa's causing the problem.

Use synaptic to see what's installed from other ppa's.
Only shows those that are still currently enabled.
May have to purge an added ppa.

---

### Post by arrrimapirate on 2013-01-28
Thanks for the reply Stinkeye!

Yes, I have the universe software sources checked, and at the moment I don't have any other PPAs downloaded.

So, the main problem here is I can't install either of the packages I need. They both say I have other dependencies that need to be taken care of.

[IMG]http://i50.tinypic.com/240yaac.png[/IMG][IMG]http://i46.tinypic.com/29mq7tt.png[/IMG]

I have both that dependency (libmagic1 5.11-2, libgtk2.0-0 2.24.13), according to Synaptic. So not sure what the deal is. The only other thing of note in my use is I live in Asia and I am downloading from the Mongolia server. Using the main server hasn't helped.

---

### Post by Cheesehead on 2013-01-28
Oops. Ignore this.

---

### Post by stinkeye on 2013-01-28
Try to fix broken packages
```
sudo apt-get -f install
```
```
sudo dpkg --configure -a
```

and then update
```
sudo apt-get update
```

```
sudo apt-get upgrade
```

Then try to install everpad again...
```
sudo apt-get install everpad
```

---

### Post by stinkeye on 2013-01-28
> **Cheesehead said:**
> pp is for Precise...12.04. Not 12.10

I thought that was just a typo which should be ppa.
Won't the command just fail using pp.

---

### Post by Cheesehead on 2013-01-28
Meh. You are right. Sorry for mistake.

---

