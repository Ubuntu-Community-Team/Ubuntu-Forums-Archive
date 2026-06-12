---
title: "ekiga and twinkle do not &quot;share&quot; sound card with others"
date: 2007-02-06
forum: General Help
---

### Post by kaleman on 2007-02-06
Hi,

I'm using Ekiga for internet telephony. Everything works perfectly well, except that Ekiga refuses to play any sounds when another application is playing sound. This way, I won't be able to hear incoming calls when I'm playing music. Twinkle seems to have the same problem.

Other applications (e.g. Skype) do NOT have this problem, so I think it's a "feature" of Ekiga and Twinkle. Does anybody know:

- if there is a workaround? Can I get Ekiga or Twinkle to play a ringtone, even if another application is already playing sound? For the actual telephone conversation I'm using a wireless headset that is exclusively for Ekiga, so the incoming call ring is the only problem.

OR

- is there another program that supports the SIP-protocol to ANY sip-provider, that does not have this problem? The SIP-client also needs to support a wireless headset. I tried a lot of other SIP-clients, including Gizmo, but Gizmo only seems to work with a Gizmo-account, and not with (additional) other SIP-accounts. I already have a sip-provider I'm satisfied with, I do not want to change that.

If anybody could answer any of the above questions I would be thankful! I AM already using ALSA instead of OSS.

Michel

---

### Post by kaleman on 2007-02-08
Back again, and solved the problem. Turned out to be very easy to solve.

I had to use the "Default" sound device instead of "nVidia NForce 2" in all my applications. 

I changed this setting both 
- in Twinkle (Edit - System Settings - Audio - Ring Tone), and
- in the System menu (System - Preferences - Sound - And then set all four choices to the option ALSA - Advanced Linux Sound Architecture).

After that, I could play music in three different applications at the same time, and still hear a ring tone!

Thanks to the ekiga-mailing list and the information on [http://wiki.ekiga.org/index.php/Getting_several_applications_using_the_sound_card_at_the_same_time_%3F](http://wiki.ekiga.org/index.php/Getting_several_applications_using_the_sound_card_at_the_same_time_%3F).

---

### Post by jerdcox on 2007-05-04
Thank you much for the information. This was a really frustrating problem, and I wasn't sure where to look for an answer. Glad to find it here.

---

