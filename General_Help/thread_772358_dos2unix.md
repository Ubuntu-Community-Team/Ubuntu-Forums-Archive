---
title: "dos2unix"
date: 2008-04-28
forum: General Help
---

### Post by big136 on 2008-04-28
Hi,
is there any equivalent of dos2unix in ubuntu ?
Many thanks.

---

### Post by jespdj on 2008-04-28
Yes, there is. Note: On [http://packages.ubuntu.com](http://packages.ubuntu.com) you can search for Ubuntu packages that contain certain files.

dos2unix is in the package named tofrodos. Install it with:
```
sudo apt-get install tofrodos
```

---

### Post by kaylus on 2008-04-28
> **big136 said:**
> Hi,
is there any equivalent of dos2unix in ubuntu ?
Many thanks.

Yes, sir. It's called dos2unix! :) You can get it by opening up a terminal (in Ubuntu, Applications->Accessories->Terminal) and then:

sudo apt-get install tofrodos

This will install the applications dos2unix and unix2dos. You can shortcut them by using "todos" and "fromdos" at the terminal, or you can set it up to do it in your GEDIT.. like this, which is something that will assist you greatly in working with the files. Follow these steps:

1. Go to Edit->Preferences->Plugins
2. Locate and check the box next to External Tools
3. Highlight External Tools
4. Click "Configure Plugin"
5. Click "New" Button

Name: Todos
Description: Convert to Dos file
Shortcut: Whatever you want
Commands: todos
Input: Current Document
Output: Replace Current Document

6. Click "New" Button


Name: Fromdos
Description: Convert from Dos Files
Shortcut: Whatever you want
Commands: fromdos
Input: Current Document
Output: Replace Current Document

Hope that helps you!

Kaylus

---

### Post by big136 on 2008-04-28
thanks to all. I installed and used todos and fromdos with any result.
My problem is that I have a file generated in Windows and I send it to Linux machine. The file has unreadable caracter when is opened in VI or by more command. Originaly they are french accented caracters : like this : é à 
But under ubuntu we see it like circled ? caracter.

Any solution ?
Thanks for help.

---

### Post by fillmore on 2009-06-10
I realize my reply may be a bit late but here it comes anyway...

dos2unix is mainly used for replacing '\r\n' (used in windows) with '\n' (used in linux).

It's possible that in your case the windows and linux machine use different character encodings and that's why your é and à characters appear scrambled.

Hope this helps.

/ fillmore

---

### Post by ratcheer on 2009-06-10
I think the problem is that you are not just dealing with a DOS to UNIX issue, you also have a Unicode file. In short, the characters are 16-bit encoded instead of just 8-bit. I don't know exactly what you need, but I am sure there are UNIX programs available that can deal with Unicode.

Tim

---

### Post by COKEDUDE on 2010-06-06
Is there a reason why dos2unix is not in the tofromdos package anymore? I already did the install command and it isn't there. 
```
sudo apt-get install tofrodos
```
[http://packages.ubuntu.com/lucid/tofrodos](http://packages.ubuntu.com/lucid/tofrodos)

---

### Post by chubinator on 2010-08-04
For anyone interested, the reason is they renamed the command from dos2unix to fromdos (and presumably todos).

---

### Post by thalia on 2010-12-29
> **chubinator said:**
> For anyone interested, the reason is they renamed the command from dos2unix to fromdos (and presumably todos).

There's a bit more to it, it depends which Ubuntu release you're using.  See bug 587973
[https://bugs.launchpad.net/ubuntu/+source/tofrodos/+bug/587973](https://bugs.launchpad.net/ubuntu/+source/tofrodos/+bug/587973)

---

### Post by JeffDavidoff on 2011-01-06
This URL [http://www.virtualhelp.me/linux/164-dos2unix-missing-ubuntu-1004](http://www.virtualhelp.me/linux/164-dos2unix-missing-ubuntu-1004) has a very helpful explanation on how to install and use dos2unix recent Ubuntu versions.

---

### Post by Dreamer Fithp Apprentice on 2011-12-20
I get this error message in trying to install a program via Synaptic:

". . . unresolvable dependencies . . . Depends: dos2unix  but it is not installable."

I've already done this:

username@linuxbox:/usr/bin# sudo ln -s fromdos dos2unix
username@linuxbox:/usr/bin# sudo ln -s todos unix2dos

Didn't change the result a bit. Is there any way to just install dos2unix either in addition to or instead of the faux version that was foisted off on us unsuspecting 10.04 LTS users? Isn't this exactly the sort of thing that should have been tried out in a non-LTS version first? Failing that, can I force a version update without having to burn a new CD? My CD drive has died on me.

---

### Post by aplonis on 2011-12-31
I have same issue. But simply substituting or replacing dos2unix via a soft link helps not at all when dos2unix as a package is a dependency in another package. Like so for makehuman-nightly build...

```

foo@Bar:~$ sudo apt-get install makehuman-nightly
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  makehuman-nightly: Depends: dos2unix but it is not installable
E: Broken packages
foo@Bar:~$ 

```

Alas and alack. I hate to say it, but at least in this case it's a good thing I also have a Windoze box.

---

### Post by oldos2er on 2011-12-31
Closed, necromancy.

---

