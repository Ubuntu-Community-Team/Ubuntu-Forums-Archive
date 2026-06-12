---
title: "Please help with SSH in nautilus ''please choose another viewer''"
date: 2007-08-22
forum: General Help
---

### Post by skelooth on 2007-08-22
For the past two years I have always mounted ssh remotely from my dev machine to work. I've done this from multiple locations, it's simple, you type ssh://name@ip into nautilus or you set it up in the 'connect to server dialog'.

I recently moved, and I am trying to connect to the server at work. Please bear in mind that this WORKED before moving just last week. When I set up the connection in the 'connect to server' dialog, the 'connecting' dialog pops up for a few minutes then dissappears with no connection being made. If I manually type ssh://name@ip into nautilus it hangs and then says "please select another viewer".

I've been pulling my hair out all morning trying to fix it. All bug reports I've found do not apply to my particular situation.

I *CAN* connect via ssh in the terminal, however it lags greatly, and freezes after a few minutes of inactivity. This is another problem that needs to be fixed.

I've tried: Deleting all user .bash* files, emptying the known_hosts file to get fresh keys, and running ssh-add

all of this has been to no avail. I really need this to work, because I really need to be able to pay my bills. The only thing that's changed is that I moved, and I'm getting a bit scared. ANY help would be VERY much appreciated.

---

### Post by skelooth on 2007-08-22
Fixed!
[https://answers.launchpad.net/ubuntu/+question/9146](https://answers.launchpad.net/ubuntu/+question/9146)

That link is what offered the solution that worked. I wish I knew why it worked, but as long as it did, I'm happy.

---

