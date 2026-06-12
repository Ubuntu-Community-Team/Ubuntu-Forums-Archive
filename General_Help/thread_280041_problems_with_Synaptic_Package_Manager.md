---
title: "problems with Synaptic Package Manager"
date: 2006-10-18
forum: General Help
---

### Post by microwave135 on 2006-10-18
Hell everyone,

I am new to the forum and to Ubuntu.  After coming from Slackware Linux, this Debian based distro is giving me some headaches.  I am using Ubuntu 4.9 on a 386 PC.

I have just recently upgraded to Dapper, and I am trying to update my system.  I need newer versions of several packages that Warty couldn't give me.

Whenever I try to apply all the new packages, Synaptic gives me the following error:

This installation run will require temporarily removing the essential package e2fsprogs due to a Conflicts/Pre-Depends loop. This is often bad, but if you really want to do it, activate the APT::Force-LoopBreak option.Internal Error, Could not early remove e2fsprogs

I know that this is a trite topic by now, but all of the current posts in all the forums I have looked in do not solve my problem.  I have tried using the forcing option.  Am I using it wrong?  I tried it 2 different ways.  This is my current apt.conf file:

// $Id: apt.conf,v 1.11 2003/02/23 16:14:11 dude Exp $
// See the apt.conf(5) man page for syntax and all available options

APT::Get::Force-LoopBreak “true”;

APT {
    Clean-Installed "false";
    Get {
        Assume-Yes "false";
        Download-Only "false";
        Show-Upgraded "true";
        Fix-Broken "false";
        Ignore-Missing "false";
        Compile "false"; 
        Force-LoopBreak “true”;
    };
};

Acquire {
    Retries "0";
    Http {
        Proxy ""; // [http://user:pass@host:port/](http://user:pass@host:port/)
    }
};


RPM {
    Ignore { };
    Hold { };
    Allow-Duplicated { "^kernel$"; "^kernel-"; "^kmodule-"; "^gpg-pubkey$" };
    Options { };
    Install-Options { "--oldpackage" };
    Erase-Options "";
    Source {
        Build-Command "rpmbuild --rebuild";
    };
};




And it still gives the same message when I run Synaptic.  What can I do to bypass this?  And why is upgrading python such a pain in the ***? ;) 

-Dave

---

### Post by microwave135 on 2006-10-19
Thanks to Redeye2 on the Linuxquestions.org forum, I discovered the problem. Here is the URL:

[http://www.linuxquestions.org/questi...d.php?t=493690](http://www.linuxquestions.org/questi...d.php?t=493690)

I hadn't read this specifically, but Ubuntu is unable to jump between package updating protocol, i.e. my switch from warty to dapper didn't work. You must upgrade in this order:

warty -> breezy -> dapper -> edgy

Im sorry if this is boneheaded common sense to the rest of the community, but I have read alot of documentation on updating package software in the last week, and this little thing was never mentioned. So, for us beginners, here is the answer.

-dave

---

