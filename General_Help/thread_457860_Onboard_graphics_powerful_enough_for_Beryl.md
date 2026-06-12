---
title: "Onboard graphics powerful enough for Beryl"
date: 2007-05-29
forum: General Help
---

### Post by orb9220 on 2007-05-29
I looking into a new motherboard. Due to money I will be limited the first couple of month's to onboard video.

Any recommends for motherboard.  Is Nvidia still the way to go or Intel?

Presently I have a nvidia FX5200 128mb agp that has served me well. But alot of the boards no longer have agp slots so....

And if anyone has links to comparisons of onboard chipset and or how they fare with Beryl.

Otherwise I would appreciate any feedback on motherboard to get in the $65-100 range.

---

### Post by renzokuken on 2007-05-29
is it just the mobo you are replacing? as in you are keeping all your processor and ram etc?

need to know what processor you have, and ram if so.

---

### Post by orb9220 on 2007-05-29
i> s it just the mobo you are replacing?

No but the mobo is what counts for compatiability. Will be getting cpu to match mobo.

---

### Post by orb9220 on 2007-05-29
bunp

---

### Post by renzokuken on 2007-05-30
with a choice between intel and nvidia onboard, its a tough choice. although i prefer nvidia, intel seem to be getting better all the time and there are also strong rumours intel is going to "open source" their drivers too. i've always used nvidia and never had problems.

i think the message really is, "anything but ATI"!

---

### Post by orb9220 on 2007-05-30
> "anything but ATI"!

Yep already new that, What I was trying to get more info on problematic mobo's.

Example: jmicron controller's, specific chipsets,sound,video,sata,etc...
I guess there is nothing specific or the right people are not seeing this thread.

---

### Post by renzokuken on 2007-05-31
from my experience, desktop mobo's are pretty infalable and easy to setup in ubuntu. i have come across a troublesome chipset yet (touch wood!!)

i would say most desktop mobo issues relate to hard drives (particularly sata) and sound cards (usually easily solved by updating alsa-driver),

but like you said, i think you need more peoples input

---

### Post by aldreis on 2007-05-31
I believe you would be well served even with a [$50 nvidia 6100](http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2000200022+107191007+1071918124&name=NVIDIA+GeForce+6100) motherboard. In fact, I happens to have one and it runs Beryl 0.2.0 at 1280x1024 quite well, for its price. ;-)

See the benchmarks ( with the proper lspci and dmesg outputs ) on the attached screenshots:

---

### Post by orb9220 on 2007-05-31
> **aldreis said:**
> I believe you would be well served even with a [$50 nvidia 6100](http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2000200022+107191007+1071918124&name=NVIDIA+GeForce+6100) motherboard. In fact, I happens to have one and it runs Beryl 0.2.0 at 1280x1024 quite well, for its price. ;-)

See the benchmarks ( with the proper lspci and dmesg outputs ) on the attached screenshots:

Is that using the onboard Video or seprate card?

---

### Post by aldreis on 2007-05-31
> **orb9220 said:**
> Is that using the onboard Video or seprate card?

Onboard, of course. See the lspci output. ;-)

---

### Post by atlfalcons866 on 2007-05-31
whats bad about ati?

---

### Post by Azakus on 2007-05-31
> **atlfalcons866 said:**
> whats bad about ati?

ATI's linux drivers don't support AIGLX, which Beryl uses to run. The only way to get an ATI card to run Beryl is to use XGL, which is buggy, slow, and is very resource heavy.

---

### Post by ArtificialSynapse on 2007-05-31
> **aldreis said:**
> I believe you would be well served even with a [$50 nvidia 6100](http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2000200022+107191007+1071918124&name=NVIDIA+GeForce+6100) motherboard. In fact, I happens to have one and it runs Beryl 0.2.0 at 1280x1024 quite well, for its price. ;-)

See the benchmarks ( with the proper lspci and dmesg outputs ) on the attached screenshots:

I have this same motherboard, and it's true, excellent onboard video. 

I'm doing the exact same thing ( lacking money to buy a new PCI-E card as my last board was AGP.  ) 

The nvidia 6100 is an excellent option.

---

### Post by orb9220 on 2007-06-01
Thanks for the Help aldreis and ArtificalSynapse. Looks like I can get this one for $75 with dual video outputs which is what I am using now on my nvidia FX5200.

[http://www.enuinc.com/mb-am2-srk-004.html](http://www.enuinc.com/mb-am2-srk-004.html)

Newegg has good prices.  But ENU has good prices and I can get there to pickup.
If you look and see something wrong with this board let me know.

Again thank you for taking the time.

---

