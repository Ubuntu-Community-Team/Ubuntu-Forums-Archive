---
title: "Firefox 3 Beta 5 Check for Updates Grayed Out"
date: 2008-05-25
forum: General Help
---

### Post by ColTom2 on 2008-05-25
Hi:

  I installed Ubunto 8.04 with WUBI. My Firefox browser 3 Beta 5 has the "Check for Updates" grayed out.

  I uninstalled Ubunto 8.04 and reinstall and still have the same problem. I have this same Beta version of Firefox on my Windows OS and I do not have this problem with it.
  
  How can I ever update Firefox in the future?

---

### Post by philinux on 2008-05-25
It will get updated via the normal update process ubuntu uses. A notification icon will appear telling you there are updates.

Simple

You can check manually two ways.

1. System Admin Update manager then click check
2. In terminal sudo apt-get update && sudo apt-get upgrade

Note this is for all software in the system not just firefox

---

### Post by shifty_powers on 2008-05-25
heh thats normal in ubuntu.

updates work a different way. ubuntu maintian repository of software, which will be checked for updates automatically by your pc.

when there is an update for firefox, the developers will allow it to be uploaded to the repository, and the update manager will let you know when it is ready ;)

bit oike windows update, but for all of your software ;)

---

### Post by ColTom2 on 2008-05-25
Thanks so much for the prompt reply, as I am new at this game!

---

### Post by shifty_powers on 2008-05-25
np's

btw check out

[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

a lifesaver for new people to ubuntu ;)

---

### Post by ColTom2 on 2008-05-25
Hi:

  I tried entering "sudo apt-get update && sudo apt-get upgrade" from the Terminal and the prompt came up asking for my user name password, but when I try to enter my sign in password I can't type it into Terminal prompt.

  I am new at this as you can tell.

 Also where can I find a list of Ubunto or Linux commands etc like the one here that you referenced? I feel like I am wondering around lost....

---

### Post by loganm10 on 2008-05-25
When you type in a password in the terminal it doesnt actually show you typing anything, its not like Windows where it will go: ******. It just doesnt show you typing, for security, so dont worry, it is accepting your keys, just not showing them for security reasons

---

### Post by Scollardical on 2008-05-25
> **ColTom2 said:**
> Hi:

  I tried entering "sudo apt-get update && sudo apt-get upgrade" from the Terminal and the prompt came up asking for my user name password, but when I try to enter my sign in password I can't type it into Terminal prompt.....

When you type your password into the terminal no letters will appear. Not even *'s. This is normal behavior. Just type your password blind. If you don't get it right then try again.

---

### Post by ColTom2 on 2008-05-25
Thanks and it worked!

Again do you have a good reference for all these Linux commands for a novice? I am trying to learn....

---

