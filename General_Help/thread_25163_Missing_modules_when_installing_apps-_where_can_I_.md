---
title: "Missing modules when installing apps- where can I get them?"
date: 2005-04-09
forum: General Help
---

### Post by Sleepy_Sentry on 2005-04-09
[http://ubuntuforums.org/attachment.php?attachmentid=692](http://ubuntuforums.org/attachment.php?attachmentid=692)


It looks like I need to install a few things so I can install ndiswrapper. Where do I get them and how do I install them?

Also, when I try to install a tar.gz it says it can't identify the file as  a tar.gz, even though it is one!

---

### Post by jdong on 2005-04-09
Please **apt-get install build-essential**, you're missing the compiler.

---

### Post by Sleepy_Sentry on 2005-04-09
That got rid of one of my errors. Thanks!

Now I have another thing I need to install. It's called module-assistant. How do I install that?

---

### Post by Sleepy_Sentry on 2005-04-09
No one can help me?

---

### Post by az on 2005-04-09
Try waiting more than an hour and ten minutes before stomping your foot.

Module-assistant is in Universe. 

Why recompile the package from source?  You will end up with the same version of the package that you already have.  If you need something newer, go to the ndiswrapper website and compile the newest version.

Like I did:

[http://apqi.com/ubuntu/ndiswrapper-modules-2.6.10-5-386_1.1-1_i386.deb](http://apqi.com/ubuntu/ndiswrapper-modules-2.6.10-5-386_1.1-1_i386.deb)

[http://apqi.com/ubuntu/ndiswrapper-utils_1.1-1_i386.deb](http://apqi.com/ubuntu/ndiswrapper-utils_1.1-1_i386.deb)

---

### Post by Sleepy_Sentry on 2005-04-09
What is the Universe? What's the command to install it?

Thanks for the help. The latest version of ndiswrapper will be a help, especially considering I'm trying to get a Linksys wireless-g USB adapter to work.

---

