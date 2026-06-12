---
title: "Can I access /tmp without booting?"
date: 2015-06-10
forum: General Help
---

### Post by Quorlia on 2015-06-10
Ok so due to a rather complicated situation my most up to date version of a file is in /tmp which was shutdown for the night. My understanding is that /tmp is cleared at boot so if I can mount it somehow I'm ok.

So my question is how? I've not got any other computers but it is dual boot with Vista. I may have a live cd. Can I do it from that?

---

### Post by QDR06VV9 on 2015-06-10
[TABLE]
[TR]
[TD="class: votecell"][/TD]
[TD="class: answercell"]The directory is cleared by default at every boot, because TMPTIME is 0 by default.

  Here you can change the time in the following file:

  </etc/default/rcS>
  TMPTIME says how frequent the tmp dir sould be cleared in days

But yes you should be able to access with Live CD
Regards
[/TD]
[/TR]
[/TABLE]

---

### Post by Quorlia on 2015-06-10
The line with TMPTIME is commented out. What does that imply? Will setting it to 1 and uncommenting it give me breathing space next time I **** up like this?

(I've saved the file elsewhere now - thanks!)

---

### Post by QDR06VV9 on 2015-06-10
> **Quorlia said:**
> The line with TMPTIME is commented out. What does that imply? Will setting it to 1 and uncommenting it give me breathing space next time I **** up like this?

(I've saved the file elsewhere now - thanks!)
Yes just uncomment the # in front and the number you choose is related to Days IE 1=one day 2=two days
Kind Regards

---

### Post by Quorlia on 2015-06-10
Great thanks for your help.

---

