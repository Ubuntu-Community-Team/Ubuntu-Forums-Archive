---
title: "Low Level Data Recovery"
date: 2008-02-10
forum: General Help
---

### Post by altonbr on 2008-02-10
So just say that a client asked you to convert her from Windows to Ubuntu and says her husband has backed everything up. Then say that when you've wiped the computer but then she calls to confirm that you backed up her e-mail. You didn't.

She was running Mozilla Thunderbird but I didn't back up her Application Settings. What's worse was that she was in Windows inside VMware on top of Ubuntu.

Is there any application, piece of hardware or a company I can call to get my hard drive read at the lowest level to see if her data still exists? It's a 300 GB hard drive and almost none of the data has been overwritten, but the partition was high-level formatted via Ubuntu's installer (ext3 to ext3).

Do I have a chance in hell? :(

---

### Post by seventhc on 2008-02-10
Possibly it wasn't set to delete from server so the mail would be there, but as far as recovering that...I'm not sure in VMware. Even if so, it would be time consuming and the software might not be cheap. There is a forensics linux, but then you also have to learn how it works, if it's even possible to begin with.

---

### Post by topsites on 2008-02-10
Yes but it's going to cost around $100 so lets just say this would be the reason I stopped offering or accepting offers to fix other people's pc's for cheap or for free :)

Best one I ever found after looking long and hard, you can try googling for others but free there isn't one that works good, most of them recover partial crap and then leave you guessing at least one letter of the filenames and what have you... The worst ones restore your stuff as file00000.001 and crap like that, this one gives you the FULL name or dang close to it if it can recover it, a pretty good program for the price... $90 may sound like a lot but it's not, the question here would be how much is this email worth to them?

[http://www.diydatarecovery.nl/irecover.htm](http://www.diydatarecovery.nl/irecover.htm)
Download the trial first, just to see how it works.
If it's just one file or one folder I think the trial is good for that, but not more.

Also you'll want to install it on a working master, then slave the destroyed drive.

> **altonbr said:**
> So just say that a client says her husband has backed everything up. Then say that when you've wiped the computer but then she calls to confirm that you backed up her e-mail. You didn't.

On a side note that's just a load of crap too.
She said her husband backed **everything** up!
End of story right there, wasn't your responsibility to back up the email was it?
Oh well heck it ain't worth getting into it, I don't think.

---

### Post by altonbr on 2008-02-11
Well, I understand that its not my fault if she said her husband backed up everything, but really meant Quickbooks, but she is a client of mine, and it never looks good to keep someone hanging dry too.

I'm really kicking myself in the **** for that one though as I COULD have easily copied over mozilla-thunderbird, but didn't. I assumed that's what her husband did.

Anyway, I appreciate the reply and I'll will check out that software when I'm back in my office. I think I have a SpinRite CD lying around somewhere, so I will try that as well.

If anyone else reads this, please please PLEASE feel free to fire off some more suggestions or stories of the same nature! Anything will help!

As for the VMware problem, those are the files I am trying to recover and once they're recovered it should be as simple as loading them up again in VMware.. I hope.

---

### Post by altonbr on 2008-02-11
Apparently there are tons of tools:

[Knoppix LiveCD]("ftp://ftp.kernel.org/pub/dist/knoppix/") (classic suggestion)
[Recovery is Possible Linux]("http://www.tux.org/pub/people/kent-robotti/looplinux/rip/")
[Ubuntu Rescue Remix]("http://ubuntu-rescue-remix.org/")
[gParted LiveCD]("http://gparted-livecd.tuxfamily.org/")
[SystemRescueCD]("http://www.sysresccd.org/")

---

