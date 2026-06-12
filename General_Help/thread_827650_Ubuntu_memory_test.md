---
title: "Ubuntu memory test"
date: 2008-06-13
forum: General Help
---

### Post by TWO on 2008-06-13
Does anyone know what the average amount of time the Ubuntu memory test is supposed to take?

I left mine running for the first time last night, after I read that running it could solve problems of Ubuntu freezing every now and again. 

I left the program running and went to bed expecting it to have finished by time I woke up. But 10 hours later, the program was still running. Is that right?

Thanks

TWO

---

### Post by Titan8990 on 2008-06-13
It actually isn't Ubuntu's memory test it is memtest86: [http://www.memtest.org/](http://www.memtest.org/). Ubuntu just packages it for diagnostic purposes.

To answer your quest memtest loops forever and doesn't stop until you stop it. Generally it is recommended that it is ran overnight like you have done.

---

### Post by TWO on 2008-06-13
> **Titan8990 said:**
> It actually isn't Ubuntu's memory test it is memtest86: [http://www.memtest.org/](http://www.memtest.org/). Ubuntu just packages it for diagnostic purposes.

To answer your quest memtest loops forever and doesn't stop until you stop it. Generally it is recommended that it is ran overnight like you have done.

Ah OK. So is there a benefit of actually running it?

---

### Post by forestpixie on 2008-06-13
Has it come up with an error - if it has then there was a benefit to running it as you know there is a problem, if it hasn't come up with an error - there's has been a benefit in running it as you know you're memory is ok at the moment :)

---

### Post by ad_267 on 2008-06-13
I'm having a similar issue maybe. I've run the memory test a few times and it always seems to go through the first two tests ok and then just does nothing on the third test and it becomes unresponsive. I only leave it running for maybe ten minutes maximum. Am I just too unpatient or is there a problem? I'm not having any problems so I don't really think there's anything wrong with my memory.

---

### Post by TWO on 2008-06-13
> **forestpixie said:**
> Has it come up with an error - if it has then there was a benefit to running it as you know there is a problem, if it hasn't come up with an error - there's has been a benefit in running it as you know you're memory is ok at the moment :)

No. No errors came up after eleven tests. All clear, so maybe that means that everything is OK?

---

### Post by forestpixie on 2008-06-13
I'd be happy. I've only used it once myself and that was by accident :)

---

### Post by mcorbett on 2010-04-04
my memory test is in constant boot loop, how do i get it out?

and i know it always loops, but when i press escape it goes back to memtest, how can i stop that?

---

### Post by mcorbett on 2010-04-04
bump, sorry, just really having issues

---

### Post by jzacsh on 2010-05-06
> **mcorbett said:**
> my memory test is in constant boot loop, how do i get it out?

and i know it always loops, but when i press escape it goes back to memtest, how can i stop that?

Did you get this resolved (I'd hope so, as its been 4 weeks :P )? If not, it sounds like a simple fix - going to your grub config and changing the default option. Also, you can probably catch the menu on boot and keep the machine from booting to its default.

---

