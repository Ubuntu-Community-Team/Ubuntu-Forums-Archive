---
title: "how to automatically remove programs?"
date: 2007-07-15
forum: General Help
---

### Post by bone2006 on 2007-07-15
After a fresh install of ubuntu and then installing say 20 programs I run this command
dpkg --get-selections > installed-software.log

Then I take the file to my other computer and I after installing ubuntu I type in:
sudo dpkg --set-selections < installed-software.log && apt-get dselect-upgrade

So now I have a clone of two computers.

My question is there a way to create a script or file that will automatically remove programs I don't use?

For instance say there's programs that come in ubuntu by default like
rythmbox
sound recorder
evoluation...................etc that I prefer not to have on the system.  

I'm looking for a way to create an ascii file that I could take to each machine to remove them automatically instead of using synaptic package manager.

---

### Post by rjfioravanti on 2007-07-15
That is difficult because they break the dependencies of the meta-package 'ubuntu-desktop'

Everything that is installed on your system by default, depends on 'ubuntu-desktop'. That kind of means the clone you created could have been achieved by just doing

sudo apt-get install ubuntu-desktop

However if you install packages on top of the default, then your clone technique would be useful


If you want to remove things like evolution, you are going to have to remove the ubuntu-desktop package, which means trouble for updating and stuff. There may be a way to remove evolution wihtout removing ubuntu-desktop, but I dont know how

---

### Post by bone2006 on 2007-07-15
Thanks for the reply
I could just leave the applications in that aren't being used.  I suppose they don't take up much wasted space

---

