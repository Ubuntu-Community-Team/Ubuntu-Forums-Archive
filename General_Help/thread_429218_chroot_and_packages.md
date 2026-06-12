---
title: "chroot and packages"
date: 2007-05-01
forum: General Help
---

### Post by yodaky on 2007-05-01
I am trying to install the debootstrap and configure it according to [https://wiki.ubuntu.com/DebootstrapChroot](https://wiki.ubuntu.com/DebootstrapChroot) so that I can build packages.  However, when I get to the portion of the guide that says to:

sudo sed -i s/dapper/breezy/g /var/chroot/etc/apt/sources.list #point apt-get to the right release

I enter:

sudo sed -i s/feisty/g /var/chroot/etc/apt/sources.list

and it returns:

sed: -e expression #1, char 10: unterminated `s' command

What am I doing wrong?  Thanx.

---

### Post by amohanty on 2007-05-01
> sudo sed -i s/dapper/breezy/g /var/chroot/etc/apt/sources.list #point apt-get to the right release

I enter:

sudo sed -i s/feisty/g /var/chroot/etc/apt/sources.list


I would suggest (as I have before and beat down for suggesting it :)) that you try to understand what you are doing before you do it. I can understand that you may not have enought time, but in the logn run you will end up saving bunches. Now to your problem:

**sed** [http://www.gnu.org/software/sed/manual/html_chapter/sed_toc.html](http://www.gnu.org/software/sed/manual/html_chapter/sed_toc.html)
is a stream editor, ie, it allows you to edit a bunch of text on the fly. What **sed -i s/dapper/breezy/g** is doing is **s**ustituting **g**(all) instances of dapper with breezy in  **/var/chroot/etc/apt/sources.list**

Now what you are doing here: **s/feisty/g** is providing an incomplete substitution command. So for example if you want to substitute edgy with fiesty in the file you would do:

sed -i s/edgy/feisty/g

OR 

sudo gedit /var/chroot/etc/apt/sources.list

and then manually replace it in the editor.

HTH
AM

---

### Post by yodaky on 2007-05-01
Thanks.  I tried reading the man and info pages but that s/edgy/feisty/g wasnt making sense.  Might be that I am so tired my eyes hurt.  Who knows.

Thanx again.

---

### Post by amohanty on 2007-05-01
IN this case per docs you need to replace :
> 
s/dapper/breezy/g

with

> s/dapper/feisty/g

HTH
AM

---

### Post by yodaky on 2007-05-01
I actually did s/edgy/feisty/g but I should be able to do s/dapper/feisty/g later and redo the apt-get update again since it only edited the sources.list

Am I correct in thinking that?  I know that might be a dumb question but I didn't really understand the reason for that command being there in the first place.  I was using a clean install of Feisty (did not upgrade from a previous version) so everything in the sources.list should have been Feisty anyway.  Atleast that is what I assume.

---

### Post by amohanty on 2007-05-01
The command is there becuase the tutorial makes some assumptions about the existing environment. So they try to provide some way to change that in case you are not in it.

Now if you have feisty, the easiest solution is to replace that step (_just_ the sed... step only) with this one:

At the command line type:
sudo gedit /etc/apt/source.list

Then replace every instance of the word **dapper** with **feisty**

Then continue on with the process.

HTH
AM

---

