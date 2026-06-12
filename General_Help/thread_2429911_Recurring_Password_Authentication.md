---
title: "Recurring Password Authentication"
date: 2019-10-24
forum: General Help
---

### Post by fester225 on 2019-10-24
On boot, Ubuntu gives me recurring password authentication demands.

How do I stop this?

---

### Post by uRock on 2019-10-25
Do you mean after you log in and start opening programs? It that's the case, then check out this link. [https://www.fosslinux.com/2561/how-to-disable-keyring-in-ubuntu-elementary-os-and-linux-mint.htm](https://www.fosslinux.com/2561/how-to-disable-keyring-in-ubuntu-elementary-os-and-linux-mint.htm)

---

### Post by fester225 on 2019-10-25
I mean that after I turn the computer on, eventually the boot process brings me to a point where I select my name as the user who wants to log in.

step 1. I'm shown my name as one of the users,
step 2. I select my name, 
step 3. I enter the password,
step 4. go to step 1.

---

### Post by ajgreeny on 2019-10-25
Does this keep on repeating, ie steps 1234, 1234, 1234, 12.... etc etc, or happen just one time, and then you are logged in?

Is this a new install or a long running installation?
Have you made any major updates, eg from one distro version to the next version?

---

### Post by fester225 on 2019-10-25
I've been running Ubuntu for about 15 years, and I'm now running the current version.

The whole point is: I never get logged in using the usual log in procedure. The system keeps asking for my password, forgets it, then asks for it again. The system would ask for my login password 200 times if I let it, and it still wouldn't be happy.

Yes, I am using the correct password. I currently get in by booting in recovery mode, and running the dpkg option, which always fails, then continuing the boot. It asks for my password and I get in. This process takes 15 minutes to a half hour, so no, I don't want to continue operating this way.

---

### Post by ajgreeny on 2019-10-25
If you use Ctrl+F2 at the login page to get to a tty command line interface, can you login there using your username and password?
PS: The password will not show as you type but type carefully and hit Enter.

---

### Post by rbmorse on 2019-10-25
Did you install with the option to bypass the need for the user to enter a password for the initial log in?   There's a known bug.  

I don't know how to fix it.  When i encountered this during 19.10 pre-release testing (pre-beta) the only recourse I found was to reinstall, but my ignorance  of GUI authentication practices is vast.

---

### Post by similar2 on 2019-10-25
How about downloading a fresh *buntu .iso and reinstalling from scratch?
It takes 20 minutes and you're done ;)

---

### Post by uRock on 2019-10-25
> **fester225 said:**
> I've been running Ubuntu for about 15 years, and I'm now running the current version.

The whole point is: I never get logged in using the usual log in procedure. The system keeps asking for my password, forgets it, then asks for it again. The system would ask for my login password 200 times if I let it, and it still wouldn't be happy.

Yes, I am using the correct password. I currently get in by booting in recovery mode, and running the dpkg option, which always fails, then continuing the boot. It asks for my password and I get in. This process takes 15 minutes to a half hour, so no, I don't want to continue operating this way.

I had that issue two days ago after a reinstall where I tried to copy /home into the active partition via live image, then rebooting. I immediately reinstalled again without formatting /home and it has worked perfectly ever since.

---

