---
title: "CD burning issue"
date: 2007-09-05
forum: General Help
---

### Post by Chondro_Biak on 2007-09-05
I have tried to burn a CD with no luck since I upgraded to Feisty... 

I have tried several different programs and none of them work, so I talked to a few friends what also use Feisty and asked them to try to burn a CD and they all have the same problem... 

When I ask it to burn it goes through the motions and says it's complete, but the CD is always blank... I then tested my CD drive on a computer with Edgy and it worked fine... 

Has anyone burned a CD since they upgraded? I normally use my flash drive or external, so I just discovered it the other day...

I'm getting  a bit frustrated...

---

### Post by ubuntukerala1980 on 2007-09-05
Try K3b

---

### Post by banewman on 2007-09-05
I use gnomebaker in feisty and it has burnt cd's ok so far - maybe ten. Both movies and op systems. Which program are you using?:)

---

### Post by ubuntukerala1980 on 2007-09-05
In gnome:

Places  -->  CD/DVD Creator

or in terminaltype

nautilus --no-desktop burn:///


:lolflag:

---

### Post by Warren Watts on 2007-09-05
> **banewman said:**
> I use gnomebaker in feisty and it has burnt cd's ok so far - maybe ten.

I had problems with Feisty burning CD's until I installed GnomeBaker.  It seemed to do the trick and I haven't had any trouble since.

---

### Post by Chondro_Biak on 2007-09-05
Thanks for the replies... 

I have tried k3b with no success... 

I have not tried gnomebaker yet... I will install that tonight and see if it works...

---

### Post by bogolisk on 2007-09-05
> **Chondro_Biak said:**
> Thanks for the replies... 

I have tried k3b with no success... 

I have not tried gnomebaker yet... I will install that tonight and see if it works...

burning disc is a problem on Feisty. It hits a variety of hardware and you seem to be part of the many people with burner that worked perfectly on dapper but not on feisty.

Ignore the recommendations from the fan-boys (who didn't bother to read the original question) who think that their beloved k3b can solve world hunger. Search forums for the threads about burning DVDs on feisty.

Summary:
[list]
[*] disc burning is broken on some hardwares with kernel from 2.6.20 and later.
[*] it's unknown if the ubuntu flavour of kernel 2.6.22 will solve this problem.
[*] the best bet is a kernel 2.6.23 but all seem to indicate that 2.6.23 won't make it for gutsy.
[/list]

Workarounds: it might take one or a combination of them. There no guarantee that the workarounds will help, because the root-cause is unknown.
[list]
[*] let's say your burner is /dev/hdd, the kill the hald poller process for that device. I.e. the process with the command line:
  ```

  hald-addon-storage: polling /dev/hdd (every 2 sec)
  
```
[*] unload the unused ata_generic module
  ```

  $ sudo rmmod ata_generic
  
```
[*] burn at lower speed (for 16x DVD burner, burn at 8x speed)
[*] modify the kernel to increase the ATAPI timeout. This requires modifying, rebuilding and reinstalling the ide-cd driver.
[/list]

---

### Post by Chondro_Biak on 2007-09-05
Now were talkin... lol

Thanks for taking the time to respond to my question... :)

Do you think this will be a problem on Gibbons? I think your saying that once Gibbons comes out I will still need to grab the 2.6.23 Kernel... Did I get that right???

---

### Post by tact on 2007-09-05
I had a similar problem - cd/DVD burning fine under Edgy but very troublesome under Feisty.

For totallly unrelated reasons I decided to do a kernel update.  (there is a thread on these forums how to do it easily) and I updated to kernel 2.6.22-9 and a very happy side effect is that now I can again happily burn DVD's...  

I have done another kernel upgrade to 2.6.22-10 and can report DVD burning still works nicely.

---

### Post by bogolisk on 2007-09-05
> **Chondro_Biak said:**
> Now were talkin... lol

Thanks for taking the time to respond to my question... :)

Do you think this will be a problem on Gibbons? I think your saying that once Gibbons comes out I will still need to grab the 2.6.23 Kernel... Did I get that right???

Well according to tact, gutsy's 2.6.22-x kernel solved the problem with **his** hardware. The issue is nobody knows the root-cause, so for **your** hardware, it's unknown until someone with that exact burner tried gutsy.

---

### Post by Chondro_Biak on 2007-09-05
So do I need to wait until October when Gibbons comes out to update my Kernel or can I do it now? 

Sounds like I can now, but I don't want to hose my computer... 

Which kernel do you suggest I try bogolisk???

---

### Post by bogolisk on 2007-09-05
> **Chondro_Biak said:**
> So do I need to wait until October when Gibbons comes out to update my Kernel or can I do it now? 

Sounds like I can now, but I don't want to hose my computer... 

Which kernel do you suggest I try bogolisk???

One of the theories was that the ide driver was broken on some hardware after 2.6.20 (or more accurately a lurking  ide driver bug resurfaced after 2.6.20.) So the workaround was to not using the ide driver for your dvd drive but to use Alan Cox's new PATA drivers.

The answer to your question is: the kernel that would have the new PATA driver needed for **your** hardware (the ide/atapi controller). It might be ubuntu 2.6.22-10 or it might be 2.6.23+.

---

### Post by tact on 2007-09-08
As bogolisk mentions the kernel upgrade did solve the problem with my hardware.  It may not solve it on your hardware.  I note too that many people have no problem burning DVD's on their hardware and the standard feisty kernels.

There is no harm in following the thread in these forms to just grab the 2.6.22-10 kernel.  Your existing kernel will still be there selectable at boot time.

---

