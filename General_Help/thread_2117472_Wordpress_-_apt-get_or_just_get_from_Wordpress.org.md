---
title: "Wordpress - apt-get or just get from Wordpress.org"
date: 2013-02-18
forum: General Help
---

### Post by allenerb on 2013-02-18
Here's a tiny bit of background - I bought my own server for doing some web hosting and I'm moving some sites from some shared hosting sites over to my server (which is Ubuntu 12.04 LTS 64-bit).  

I've installed Wordpress using the apt-get install WordPress and going about things by creating symbolic links to the shared directory and all that, however, I found that when doing things this way, WordPress has been modified to do some special things for the Debian/Ubuntu setup - so porting sites over is a bit of a pain.  

Now here's my question - why would I not just copy down WordPress from the main WordPress.org site and set up my sites that way?  I'm assuming the only real reason is I could do an apt-get upgrade to pull the latest files and update all my sites at once?  Is there any other reason?  Am I missing something?  Wordpress isn't all that difficult to set up anyways so why would I concern myself with doing an apt-get?

Thanks in advance for any insights,

Allen

---

### Post by tgalati4 on 2013-02-18
I would presume that the repository version is built/configured for your 12.04 operating system.  The version you pull from the website may be the same or it may be newer and you will have to do the configuration.

An alternative installation method is to use *stacks*.  These are statically-built versions that install easily and you could actually have multiple installs on the same machine--which may help in your situation.  Stacks take more physically hard disk space (because each stack contains the libraries as well, no shared libraries), but disk space is usually not a problem.

[http://bitnami.org](http://bitnami.org)

For information purposes, on 12.10:

tgalati4@Mint14-Extensa ~ $ apt-cache policy wordpress
wordpress:
  Installed: (none)
  Candidate: 3.4.2+dfsg-1
  Version table:
     3.4.2+dfsg-1 0
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal/universe amd64 Packages

---

### Post by allenerb on 2013-02-18
Thanks tgalati4,

That's pretty much what I was wondering...So would it be safe to say that the apt-get install is used simply because it takes less space and allows the sharing of a code base?  The whole reason I started asking the question is because all the tutorials out there show the apt-get install method for WordPress on Ubuntu...

I mean, there's no reason I couldn't just set up my own /etc/wordpress folder with the latest release, create symbolic links to that directory to use a shared codebase, correct?  

Thanks again - just trying to make sure I keep my server easy to manage while at the same time having the best possible solution for moving forward.

---

### Post by SeijiSensei on 2013-02-18
One of the advantages of using repository versions is keeping up-to-date with newer releases.  That's not really applicable to WordPress which tells you an update is available when you're on the blog's Dashboard page.  Installing updates from within WordPress is so easy that I don't see a big advantage to relying on the repositories.  If anything, I would think the native WordPress process would be more up-to-date since no one has to repackage the updated version for the repositories. I speak from experience having just recently updated to 3.5.1 by clicking a few links and buttons.

---

