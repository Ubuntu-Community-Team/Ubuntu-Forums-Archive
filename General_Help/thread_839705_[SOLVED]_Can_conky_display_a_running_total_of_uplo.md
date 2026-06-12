---
title: "[SOLVED] Can conky display a running total of upload/download in MB?"
date: 2008-06-24
forum: General Help
---

### Post by timzak on 2008-06-24
I saw a cool screenlet that shows "total uploaded/download this month" and wondered if this was something conky could do.  I'd like this to somehow differentiate between network transfers and internet transfers.  That screenlet adds in file transfers between computers in the home network, so it throws off the accuracy of wanting to see how many MBs are uploaded and downloaded each month.  I started using it and shortly after, I moved a couple of gigs of music from one computer to another in my home network, then noticed these were added into the screenlet's running total, which made it impossible to know how much I actually downloaded from the internet.

Any idea if this can be done?

Thank you so much for your time.

P.S. I already use conky to show network transfer speeds in real time, so I'm aware that conky can do this.

---

### Post by timzak on 2008-06-25
*bump*

Can anybody help me?  I think this can be done in conky, but need help with the coding.  I'd like it to look something like this:

Monthly Totals
Upload:  xx Megabytes
Download:  xx Megabytes

If possible, I'd like this to show only *internet* transfers and to exclude any home network transfers.

Thanks.

---

### Post by Doji on 2008-06-25
Edit: Scratch that, this isn't a monthly total. Got to learn to read... There doesn't seem to be a way to do it. Maybe if somebody wrote a script, similar to how they do weather in conky, but that's beyond me.



Yes, it's possible, but it "overflows at 4 GB on Linux with 32-bit arch and there doesn't seem to be a way to know how many times it has already done that before conky has started."

At any rate, you can use $totalup and $totaldown in your conkyrc.

For more conky variables go to [http://conky.sourceforge.net/variables.html]("http://conky.sourceforge.net/variables.html").

---

### Post by timzak on 2008-06-25
Thanks, Doji.  That 4GB limitation kind of bursts my bubble for wanting to try.  You know, I think that the screenlet app that does this has the same limitation.  Probably just a general 32-bit Linux limitation.

At any rate, thank you for your reply.

---

