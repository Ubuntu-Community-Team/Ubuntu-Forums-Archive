---
title: "Suddenly, printing no longer works!"
date: 2006-08-27
forum: General Help
---

### Post by dv_ on 2006-08-27
Hi.
I have an Ubuntu box (a P4 2.4GHz), connected to a router (a 200MHz P2). CUPS is installed on the router, and my Brother HL1430 laser printer is connected to it.
When I installed Dapper, printing worked flawlessly, as it does in Windows (I use a direct ipp connection in both systems). I use the hl1250 printer, which worked fine.
But suddenly, after the last dist-upgrade, printing in Dapper no longer works! No matter what I send to the printer, this is always the result:

```

-12345X@PJL
@PJL JOB NAME="Ghost"
@PJL SET ECONOMODE=OFF
@PJL SET MEDIATYPE=REGULAR
@PJL SET SOURCETRAY=AUTO
@PJL SET RESOLUTION=300
@PJL SET RAS1200MODE=OFF
@PJL ENTER LANGUAGE=PCL
126A126A10o010E1-120Ur..... <a string of random chars continues here>

```

I am *really* confused. In Windows, printing still works fine, nothing changed there. Telling CUPS on the router to print a test page works, it gets printed successfully. Therefore I can rule out problems in the router. Does anybody have an idea what is going on here?

---

### Post by AlterEgo on 2006-08-27
Are you sure you are not suffering from:
[http://ubuntuforums.org/showthread.php?t=240549&highlight=brother+print](http://ubuntuforums.org/showthread.php?t=240549&highlight=brother+print)

---

### Post by dv_ on 2006-08-27
No, this is different. It does print a page every time I send a print request, its just that the code I posted gets printed, no matter what I actually wanted to print.

The router (the P2) runs an old Gentoo version (I don't want to touch it - it took me weeks to get it running). Now, maybe if the CUPS version installed on my Ubuntu machine (the P4) is somehow incompatible with the CUPS version on the router, this could explain things. But I am not aware of incompatibilities of this kind.

EDIT: I see now that someone else had this problem: [http://www.ubuntuforums.org/showthread.php?t=242485](http://www.ubuntuforums.org/showthread.php?t=242485)

---

