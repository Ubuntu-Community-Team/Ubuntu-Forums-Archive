---
title: "What should be checked here?"
date: 2007-12-23
forum: General Help
---

### Post by mmilitia9 on 2007-12-23
Hey guys..Take a look at the screenshot.  What should be checked?  all four?  I never changed any of this before.. but I was wondering why the top two arent checked as well.

Also.. When I go to update manually.. I get this error message

W: GPG error: [http://apt.cerkinfo.be](http://apt.cerkinfo.be) unstable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A35A4E6EF00175CA

What should I do about that?

---

### Post by vayde on 2007-12-23
Those are the Canonical 'partner' repositories.  As I understand it, those are packages offered by corporate partners of Canonical.  If you want to use software from those repositories, check them.  You're not going to be missing anything critical to the function of your computer by leaving them off.

I would guess that they're not enabled by default because many of the people in the open source community feel strongly about free and open source software, and may not want the repositories enabled by default, or there may be legal reasons.  

'Source' repositories are the source code for the programs, not the precompiled packages.  You won't need those unless you're going to do development work, or somehow hack the source code.

Your second question:  You're getting the error message because your machine doesn't recognize the public key of that repository as a trusted source for software.  There should be instructions on the repo's website for obtaining and installing their key if you decide to trust them.  

cheers.

---

### Post by mmilitia9 on 2007-12-23
Can't find anything on the website about trusting them... It obviously worked finebefore.. I never messed with anything in these options before until that issue came up and started to display.. Hmm.. could you give me a hand and figuring out?

---

### Post by vayde on 2007-12-23
Unless I miss my guess, you can install packages from that repo without problems, it's just going to complain about not having the public key.

If you go to the site indicated my the link in your original post, you'll see a couple of cryptic lines near the top:

gpg --keyserver hkp://wwwkeys.eu.pgp.net --recv-keys F00175CA
gpg --armor --export F00175CA | sudo apt-key add -

Those are the commands that will retrieve, and add that repository's public key, and install it on your system.  

Note however, that above those lines it says that their packages probably wont work with ubuntu.  If you paste those two lines into a terminal window, and run them, you'll have it set up.  (paste the first line, hit return, paste the second line, hit return)

If you want to play it safer, and don't want to use the repository, then you'll need to open the file: /etc/apt/sources.list in your favorite text editor.  Look for the line containing that repo's url, and remove it.  You'll need root privileges to modify that file, so use sudo.

Afterwards run 'sudo apt-get update' to replenish your cache, and you shouldn't see the error message again.

let me know if you need more specific instructions.  We never know how new someone is.  Likewise, apologies if the above is to pedantic.

cheers.

---

