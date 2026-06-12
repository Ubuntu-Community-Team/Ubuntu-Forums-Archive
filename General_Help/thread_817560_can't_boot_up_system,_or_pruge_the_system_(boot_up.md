---
title: "can't boot up system, or pruge the system (boot up problem or hard drive problem??)"
date: 2008-06-03
forum: General Help
---

### Post by eric225 on 2008-06-03
Okay, I'm a noob at ubuntu just to get this started so when answering make sure its very precise or I wouldn't know how to do it...

Okay anyway, a week ago I for some reason (seemed like a good idea at the time) started to take apart my laptop. I couldn't get the whole thing open for something in the middle of it was still screwed in. So I gave up and put everything back to together again. I used the laptop for about 3 to 4 runs of windows before it stopped working. Grubs isn't there anymore. It says something about MBA, (which should of been overwritten after ubuntu was installed). After that it goes "Operating system not found". I tired reinstalling grubs, tired installing other OS booters. Also I have tired wiping the entire system. Windows after asking for language and "Are you sure to delete all of your files" and accepting that. It does an error and terminates the "perge". Ubuntu goes all well till parshing the drive. If I try to use the whole hard drive it goes to the pre-loading/installing and then has an error. If I try to make another parshion it says that it needs a root, but it also knows that the other OS's are still there because it says it has only the amount of space left as I did in windows. (Doesn't say the OS's are there, just that the space is used). 

I don't know what to do!! I have tried a lot of things and got no results (except maybe a headache). Sorry about the 'noob' talk about computers but I just never remember the terms right. (Also for the terrible spelling)

If someone can revive my laptop I'll believe in god again!! (jk)
I'll just be really really greatful and know there are kind-hearted souls out there still.

---

### Post by wpshooter on 2008-06-03
The first thing that I would like to ask is the WHY you were attempting to take the laptop apart ?

And that leads to my second question, which is, do you know for a fact that you have everything back together like it should be and subsequently if you have somehow damaged some hardware of the computer, I don't care what O/S you may put on it, it is probably not going to operating correctly until the hardware is up to par.

Thanks.

---

### Post by cariboo on 2008-06-03
Sounds like you've got a flakey hard drive connection. I'd check that first before doing anything else.

Jim

---

### Post by wpshooter on 2008-06-03
> **cariboo907 said:**
> Sounds like you've got a flakey hard drive connection. I'd check that first before doing anything else.

Jim

Yes, I agree.  If this is one of the components you played around with, the connector on the hard drive would be the first thing to check.  But be very careful, I don't believe taking LAPTOPS apart is a task for the untrained.

---

### Post by sports fan Matt on 2008-06-03
I have to reinstate the asked question..Why in the world would you take a laptop apart??? "seemed like a good idea at the time"? Im stammering here, cause im imaging this...And my .02 is..I hope its under warranty cause even IF it miraciolously boots up, the messing you did could have purged the system...

---

### Post by Sef on 2008-06-03
> Okay anyway, a week ago I for some reason (seemed like a good idea at the time) started to take apart my laptop.

We have all done things that seemed like a good idea at the time.  Just take this as a learning experience.

---

### Post by Lord Xeb on 2008-06-03
I have taken my laptop apart before and nothing happened. As long as you make sure all the screws are down snug (the screw should be about a quarter turn to half turn passed finger tight), you are good. Before you take it apart again, check and see if it is the HDD is bad (or if the connection is bad by taking it out then putting it back in again). If that works and you are able to boot, but you still get an error and want to try a fresh install, try this command in root once in a live cd (note: It will shred you entire contents of your drive and overwrite everything with zeros which means there will be nothing left. It will  be like a new HDD):

```
# shred -vfz -n 100 /dev/sda
```

Change the number "100" to something like 5 or 10. That will take care of your HDD. Then do a fresh install and see what happens.

Again, the above command will be like you shredding some paper multiple times, then creating new paper out of the shreddings.

 Also, if something doesn't want to come, do not be forceful. If you used any kind of force and it doesn't want to come (I mean you were more than gentle), you may have broken something. Try and take apart your laptop again by removing the battery, cd drive, hard drive, and anything else that can be removed (even the ram, for it can get damage in the taking apart process). Be gentel (and I mean gentle) and unscrew everything that is on the case (except the screws around the monitor). There are little plugs that hide screws. Also, once you take the screws out, flip it back over. The keypad comes off and the the touch pad part comes off aswell. Look and make sure all the connections are good (like wires and stuff like that), examin the main board for cracks, then put everything back together. Put all the wires and connectors back, screws back in snug (but not too tight. Once you get the screws screwed down finger tight, do a quarter turn to a half turn  passed finger tight for a them to be snug. Nothing more). If it doesn't boot, go back and check all the screws. Also, check all the removable parts (the hard drive, cd drive, etc...). If it still doesn't boot, then you are officially SOL.

---

