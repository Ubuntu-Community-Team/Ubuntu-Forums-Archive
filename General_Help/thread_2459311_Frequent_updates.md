---
title: "Frequent updates"
date: 2021-03-16
forum: General Help
---

### Post by alainhenry on 2021-03-16
Since a few months, I have a feeling Ubuntu updates are much more frequent, like every other day or so. 
Possibly, this dates from the latest upgrade to 20.10. 
Any idea why this happens ?  Could it be that I changed the update frequency in my settings (it's now on daily, I don't remember what it was before) ? Or was there a change in policy at Ubuntu ? 
Can I set the update frequency to weekly without increasing the risk too much ? 
Thanks for any comment/suggestion on this.
Alain

---

### Post by Impavidus on 2021-03-16
The number of upgrades per week varies a bit, depending on dev activity. Around Christmas it's normal to see no upgrades at all for a few weeks. You can set upgrade frequency to weekly, but that won't affect your total number of upgrades. They will just come with more at a time. It's not very likely the same package gets upgraded twice in one week. The older your Ubuntu release is, the less upgrades you'll get, as there're less bugs left to fix.

If you wish, you can read your logs and count the number of upgrades per week for the past 8 months. In /var/log/dpkg.log*, every line with "upgrade" right after the timestamp indicates one upgrade.

---

### Post by ActionParsnip on 2021-03-16
If memory serves (Not used vanilla Ubuntu in a while) the apt system checks the packages for you regularly but the user (you) must enter their credentials to approve installation. If security issues and bugs are found and squashed in many packages then more packages will be downloaded and installed when you authorize it. This is good and it's great that you are keeping your OS up to date.

---

### Post by gj48 on 2021-04-01
I have Ubuntu 20.04 LTS. The past few months I have been getting small (less than 1 MB) updates anywhere from 1-3 times per day. Larger (up to about 80 MB) updates have been happening at least once per week. I now have changed the frequency from check and notify daily to instead automatically download and install security updates but to check for and display other updates every 2 weeks.

---

### Post by mikewhatever on 2021-04-01
Nah, I have a feeling it is alright. Don't fix what's not broken.

---

