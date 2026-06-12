---
title: "Update Problem"
date: 2015-08-18
forum: General Help
---

### Post by dieselglock on 2015-08-18
Hello I have been away from Ubuntu for a while and am having trouble with updates. I have read some of the threads on the subject but cant really understand or follow what do do.

I get a message that not all updates good be installed and something about doing a partial upgrade that I have not done. I do not want to upgrade from 14.04 at this time. 

I am lost here please help.

Lenny

---

### Post by TheFu on 2015-08-18
Which release are you on today? Support for 10.04 desktop ended 2+ yrs ago.

The general solution is to patch weekly with these 2 commands:
```
sudo apt-get update
sudo apt-get dist-upgrade
```

If you don't do that, eventually new software will refuse to be installed due to dependency issues.

12.04 is LTS too and supported for 5 yrs from the release ... so 12+5 = 2017.

---

### Post by dieselglock on 2015-08-18
> **TheFu said:**
> Which release are you on today? Support for 10.04 desktop ended 2+ yrs ago.

The general solution is to patch weekly with these 2 commands:
```
sudo apt-get update
sudo apt-get dist-upgrade
```

If you don't do that, eventually new software will refuse to be installed due to dependency issues.

12.04 is LTS too and supported for 5 yrs from the release ... so 12+5 = 2017.

Hello I am running 14.04

---

### Post by TheFu on 2015-08-18
> **dieselglock said:**
> Hello I am running 14.04

Ah - I see that now. Sorry, I missed it in the OP.  Your profile still ways 10.04 and I misread it to be you did not want to update to 14.04 from that version.

Run those 2 commands in my prior post, please. Any issues?

---

### Post by dieselglock on 2015-08-18
> **TheFu said:**
> Ah - I see that now. Sorry, I missed it in the OP.  Your profile still ways 10.04 and I misread it to be you did not want to update to 14.04 from that version.

Run those 2 commands in my prior post, please. Any issues?

That seems to have worked as far as I can tell. Thank you for your help.

Lenny

---

