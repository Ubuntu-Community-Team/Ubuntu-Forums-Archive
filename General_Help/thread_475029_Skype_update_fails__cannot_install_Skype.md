---
title: "Skype update fails / cannot install Skype"
date: 2007-06-15
forum: General Help
---

### Post by diana.artemis on 2007-06-15
I'm using Dapper, and had Skype installed and working well. I've just had an update notification, and ran the update manager.  It failed to update Skype because of a problem with dependencies.  I tried uninstalling and reinstalling Skype, but that now fails too.

Here's the error message:

#######
The following packages have unresolvable dependencies. Make sure that all required repositories are added and enabled in the preferences.

skype:
  Depends: libasound2 (>1.0.12) but 1.0.10-2ubuntu4 is to be installed
  Depends: libc6 (>=2.3.6-6) but 2.3.6-0ubuntu20.4 is to be installed
  Depends: libgcc1 (>=1:4.1.1-12) but 1:4.0.3-1ubuntu5 is to be installed
  Depends: libqt4-core (>=4.2.1) but 4.1.2-1ubuntu1.1 is to be installed
  Depends: libqt4-gui (>=4.2.1) but 4.1.2-1ubuntu1.1 is to be installed
  Depends: libstdc++6 (>=4.1.1-12) but 4.0.3-1ubuntu5 is to be installed
########

I do have the Skype repository enabled in /etc/apt/sources.list as follows:

deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free

I'd be grateful for any advice.

---

### Post by mikewhatever on 2007-06-15
A program, such as skype, may need additional packages to run, unrelated to it. Go to System>Administration>Software Sources and enable Universe and Multiverse repositories.

---

### Post by diana.artemis on 2007-06-15
Mikewhatever >>> Thanks for your quick reply.  I do have all the repos enabled.  I'm beginning to think that the dependencies in the new Skype package may be wrong - or wrong for Dapper.  If this isn't fixable (and I don't know how it might be) I guess I either stop using Skype on my laptop, or wait till the Skype team gets it sorted out.

But someone may have a good workaround...

---

### Post by arthurD on 2007-06-16
you can use the static binary from the skye download page.

---

### Post by arthurD on 2007-06-16
Btw, does anyone know, how can I add a application to the menu, what I have installed "by hand", like the static skype executable?

---

### Post by diana.artemis on 2007-06-17
> **arthurD said:**
> you can use the static binary from the skye download page.

Thanks, arthurD.  I think you're right - that's the only way to do it.  If I understand the error message  from update manager correctly, the Skype update from their site calls for some lib files, but the dapper repo has only older versions of the ones the Skype package is specifying.  I guess the right ones will be included in the static binary?

(BTW, I've checked this in Edgy and Feisty - same problem with both.  So I guess the issue is to do with the Ubuntu repos lagging behind the Skype 1.4 upgrade?)

---

### Post by arthurD on 2007-06-17
In the static binary the libraries are "build in", therefore independent, from the ones on your system. ( the binary is bigger though then an dynamically build one)
However, I had the same problem as you, and this did the trick. Just follow the instructions in the README file. You have to add also a launcher to the panel yourself.
I haven't figured out yet how to add one to the Applications/Internet menu, but I'll post it here once I have.

---

### Post by diana.artemis on 2007-06-18
arthurD >>> Thanks for your advice and help.  I've currently got a problem with booting my laptop after upgrading it Dapper > Edgy > Feisty;  when I've got that sorted out, I'll be in a position to try again with Skype.

---

### Post by warcriminal on 2007-06-18
Here is a short tutorial on how to install and configure Skype 1.4 for Linux.

It's a lot simpler to follow than the "official" Skype installation guide.

[http://www.goitexpert.com/entry.cfm?entry=Skype-Releases-v14-for-Linux](http://www.goitexpert.com/entry.cfm?entry=Skype-Releases-v14-for-Linux)

---

### Post by diana.artemis on 2007-06-19
arthurD / warcriminal >>> Many thanks for your helpful advice and suggestions.  I've been having serious problems with Feisty kernel 2.6.20 on my old Dell Inspiron laptop (an issue to do with the kernel not detecting the CD drive properly - others have had similar issues with 2.6.20 not recognising hardware that earlier kernels recognised).

   Anyway, I've reverted to kernel 2.6.17, and all is back to normal (I hope!).  But the hassles have made me anxious about trying Skype 1.4.   The dire warnings on the site you sent a link for, warcriminal, about 1.4 still being seriously alpha and bleeding edge have put me off.  So for now I've reinstalled 1.3 from the medibuntu repo, and it's working fine.

   I'm very grateful for your readiness to help, and feel a bit apologetic for not taking the plunge.  Hope you appreciate my misgivings!

Best wishes

---

### Post by arthurD on 2007-06-20
arthurD stands for Arthur Dent from the "hitchhikers guide through the galaxy", zaphodB was used.

---

### Post by jlh on 2007-07-05
The static installation is a piece of cake.  Just download and extract.

---

