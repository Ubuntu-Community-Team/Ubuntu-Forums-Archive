---
title: "Installing pre-shellshock openshh-server"
date: 2015-04-25
forum: General Help
---

### Post by Robing Goodfellow on 2015-04-25
I'm writing a paper for my pen testing class that details the shellshock bug of last fall. Details:
Host machine is running 64 bit Trusty
Running Virtual box
Virtual machine running Kali
Virtual machine running Maverick

The idea is use either Kali or Trusty to hack into Maverick, use the shellshock bug to get into the system. That's the easy part.

Here's the hard bit:
The network works fine, all 3 machines can ping and see each other.
All ports on Maverick are closed (I've done little to no configuring, absolutely no updating).
I want to open port 22 (ssh) to give me an in for the demonstration.
sooooo I need to install openssh-server
Should be no problem, but I'm getting nowhere:

```
Reading state information... Done
package openssh-server is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or is only available from another source

E: Package 'openssh-server' has no installation candidate
```

I'm figuring that, because Maverick is no longer supported I'm having this problem???
If so, any work arounds / ideas?

regards, Richard

---

### Post by Robing Goodfellow on 2015-04-25
I'm doing a project for my Masters that documents and demonstrates the shellshock vulnerability (in a vm). In another thread [http://ubuntuforums.org/showthread.php?t=2275362](http://ubuntuforums.org/showthread.php?t=2275362) I'm seeking help to do this with Maverick. I chose Maverick because it's obviously vulnerable, but if I can't get openssh installed on it (that's the question in the other thread) because it is no longer supported (I suspect this to be the cause of my woes) then my question here is:

As the shellshock patches didn't come in until 8 months after Precise was released, if I use Precise instead would it install vulnerable? In other words, do the maintainers go back and change the original code as well as send out the patch in updates (bad for me) or are patches only released in updates (good for me, I don't want it patched)?

regards, Richard

---

### Post by egeezer on 2015-04-25
Would this help?
[http://old-releases.ubuntu.com/releases/](http://old-releases.ubuntu.com/releases/)

---

### Post by coffeecat on 2015-04-25
Let's keep this all in one thread since the question is: how do you install pre-shellshock openssh-server in Ubuntu. The actual release doesn't really matter.

Threads merged and thread title changed..

Egeezer is correct in that the old-releases repository is probably your best bet, but the actual link won't help as that leads you to old ISOs.

You've got two options.

Use this link - [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades) &#8211; to change your sources in Maverick. You don't need to upgrade &#8211; all you need is the edit to sources.list.

Or have a look here:

[http://old-releases.ubuntu.com/ubuntu/pool/main/o/openssh/](http://old-releases.ubuntu.com/ubuntu/pool/main/o/openssh/)

That's got versions of openssh-server going back to 2004. You can download them and then install them manually, but the trick would be to match the version of openssh-server to the Ubuntu release it belongs to.

Have fun!!

---

### Post by Robing Goodfellow on 2015-05-20
Thanks for all the help!

---

