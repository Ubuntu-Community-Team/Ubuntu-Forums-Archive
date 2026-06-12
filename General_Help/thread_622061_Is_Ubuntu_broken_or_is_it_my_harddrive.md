---
title: "Is Ubuntu broken? or is it my harddrive"
date: 2007-11-24
forum: General Help
---

### Post by sam_uk on 2007-11-24
Installed Gutsy on a [https://wiki.ubuntu.com/LaptopTestingTeam/HPNX6325](https://wiki.ubuntu.com/LaptopTestingTeam/HPNX6325)

It works great for about 30-40 minutes and then the harddrive becomes very active. The light comes on and it makes harddrive like sounds. This continues for several minutes, during this time the system becomes very unresponsive. Sometimes this will continue for more than ten minutes at which point I am forced to do a hard reboot. (ctrl-alt-backspace has no effect).

This behaviour is not exhibited on the same laptop using other OS's. Debian works fine on it.

Could this be a bad sector on my disk? or is it something that others have experienced with Ubuntu?

When I have had top or system monitor open during these episodes no unusual processes are seen.   It happens seemingly at random when using different applications.


here is

 smartctl --all /dev/sda
[http://pastebin.ca/795935](http://pastebin.ca/795935)    

Any help gratefully received. I really like all the compiz eye candy and do not want to have to go back to Debian..

Thanks

Sam

---

### Post by runemaste644 on 2007-11-24
Well try the memtest tool on the 7.10 LiveCD. That will show if you have any problems.

---

### Post by HermanAB on 2007-11-24
Run the 'top' utility and see what bubbles to the top of the list:
$ sudo top

Cheers,

Herman

---

### Post by sam_uk on 2007-11-24
> **HermanAB said:**
> Run the 'top' utility and see what bubbles to the top of the list:
$ sudo top



As I said in my post
"When I have had top or system monitor open during these episodes no unusual processes are seen. It happens seemingly at random when using different applications."

I see normal activity in top.

---

### Post by ryanVickers on 2007-11-24
I think by default Gutsy comes with the indexing tool enabled - try turning off "tracker"

It just seems stange to me it would totally lock up like that... :confused:

---

### Post by sam_uk on 2007-11-24
I think by default Gutsy comes with the indexing tool enabled - try turning off "tracker"


OK done, I will let you know if it happens again.

I tried memory test and it finished with no errors.

Thanks for the help so far..

---

### Post by sam_uk on 2007-11-25
even with the tracker turned off it still does it :(

---

### Post by sam_uk on 2007-11-25
There are lot's and lot's of these in kern.log and debug

Nov 25 13:43:31 sam-laptop kernel: [60655.644000] APIC error on CPU0: 40(40)


I also tried turning off anacron

---

### Post by rbmorse on 2007-11-25
What's your swap usage look like?

---

### Post by sam_uk on 2007-11-25
> **rbmorse said:**
> What's your swap usage look like?


Not sure how would i check?

It just happened again and this is in /var/log/kern.log

Nov 25 14:18:28 sam-laptop kernel: [62752.376000] Buffer I/O error on device hda, logical block 2246145

---

