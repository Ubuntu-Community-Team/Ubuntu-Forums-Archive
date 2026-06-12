---
title: "Clarification"
date: 2008-05-29
forum: General Help
---

### Post by NightShade01 on 2008-05-29
Ok this might seem like a completely stupid question but I'm not understanding.  So I have been using ubuntu desktop and server for a while now and have used and seen unix (solaris) servers.  What I don't get is....what's the different?  I get the history behind linux vs unix but what are the real differences say in unbuntu's server vs opensolaris.  Any insight would be helpful.  Sorry again if this sounds like a stupid question.:confused:

---

### Post by HalPomeranz on 2008-05-29
This is one of those classic "blind men and the elephant" type questions.  Depending on what level of the system you're dealing with, you'll come up with different answers.

-- If you're just glancing over somebody's shoulder at what's on their screen, Ubuntu and Solaris look very different.  This is primarily due to different choices in default window managers, widgets, and window decoration.  Ironically, "under the hood" both are being driven by X servers that evolved from a common code base.

-- On the command-line level, there's a lot of similarity, mostly because Solaris is starting to incorporate a lot of the GNU versions of various commands and because everybody's trying to conform to the POSIX standards.  But you still stub your toe on various differences from time to time.  One that gets me all the time, for example, is that the Solaris tar command doesn't have built-in gzip/bzip functionality like the GNU/Linux version does (though you can run "gtar" on recent Solaris releases to get the GNU version).

-- If you're a Sys Admin, things start looking really different.  There are different start-up conventions (/etc/rc.d/* vs. Solaris SMF, etc), different package managers and patch update processes, the use of sudo vs. su, radically different device configuration mechanisms, and so forth.  Solaris has some "enterprise" level features that I wish Linux had like Dtrace and process resource controls, and I wish Sun's ZFS file system was integrated into the Linux kernel.  OTOH I wish the Solaris kernel implemented Linux features like reverse path filtering and SYN cookies.

-- Security configuration between the two platforms is also radically different.  In Linux you've got AppArmor/SELinux/grsecurity vs. Solaris process privilege controls and Role Based Access Controls.  The kernel-based stack protection implementations are wildly different (the Linux implementation is stronger).  You've got different kernel-based firewalls on each platform-- IP Tables on Linux and IP Filter on Solaris.  PAM configurations vary wildly.  The differing "Sys Admin" interfaces between the two platforms also makes security configuration different on each type of machine.

-- If you're a programmer or software maintainer there can be substantial differences between the two systems as well (especially if you're dealing with kernel-level code).  I dread having to port Open Source software to the Solaris platform because most developers these days assume their software will only be compiled/used on Linux platforms and have built-in assumptions about programming interfaces and libraries that are always available in Linux (glib, gtk, etc) but not so common on Solaris.

Hope this helps clarify things for you...

---

### Post by NightShade01 on 2008-05-29
Yes very much so thank you.  I think the problem is that I haven't used Solaris for server work as much as the Ubuntu server (mostly because I enjoy unbuntu very much :))  I never really noticed from an administration point the differences (although I haven't had much experience in a corporate environment yet either).  I guess will start to notice those differences depending on the company that I choose to work for and what systems they use.  Thanks again.

---

