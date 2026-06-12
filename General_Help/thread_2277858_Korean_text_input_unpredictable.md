---
title: "Korean text input unpredictable"
date: 2015-05-12
forum: General Help
---

### Post by palmgrower on 2015-05-12
I have 3 PC's. All have 15.04 fresh installation, not upgrade. All have Korean as the base language. Results are different. PC 1: Korean was installed and Korean input started working immediately. PC 2: Korean was installed but I had to run ibus-setup in terminal to make Korean input work. PC 3: Korean was not installed. Added Korean in Language Support. Still no Korean. Removed and reinstalled Korean. Finally got Korean installed. ibus-setup in terminal didn't work. From Text Input, select/deselect Korean (Hangul) and Korean (101 keys). I have no idea why such differences. I came to the conclusion to try different combinations, adding/deleting Korean, running ibus-setup in terminal, selecting/deselecting Korean, Korean (hangul), Korean 101 Keys. 

If anyone knows the best method, please let me learn. Thanks.

---

### Post by workman7292 on 2015-05-12
&#54620;&#44397;&#48516;&#51060;&#49884;&#47732; &#54620;&#44397;&#50612;&#47196; &#54616;&#44192;&#49845;&#45768;&#45796;.

ibus&#47484; &#49324;&#50857;&#54616;&#49888;&#45796;&#47732; ibus-hangul&#51012; &#49444;&#52824;&#54616;&#49901;&#49884;&#50724;.
# sudo apt-get install ibus-hangul

&#47196;&#44536;&#50500;&#50883; &#54980; &#54620;&#44544; &#51077;&#47141; &#44032;&#45733; &#54633;&#45768;&#45796;.
&#50500;&#47000; 3beol ppa&#47484; &#51060;&#50857;&#54616;&#49884;&#47732; &#48372;&#45796; &#44036;&#54200;&#54616;&#44172; &#54620;&#44544; &#51077;&#47141; &#44032;&#45733;&#54633;&#45768;&#45796;.

&#54620;&#44397; &#50864;&#48516;&#53804; &#47784;&#51076;&#51012; &#51060;&#50857;&#54616;&#49884;&#47732; &#48372;&#45796; &#46020;&#50880;&#51060; &#46112; &#44163; &#51077;&#45768;&#45796;.
[http://forum.ubuntu-ko.org/](http://forum.ubuntu-ko.org/)

Are you korean! me too.

Using the ibus, you just install ibus-hangul.
After logout, going back possiblity input korean.

It's better method is use the 3beol ppa.
# sudo add-apt-repository ppa:createsc/3beol
# sudo apt-get update && sudo apt-get ibus-hangul

Use the 3beol better useful.

---

### Post by palmgrower on 2015-05-13
Thank you for the tip. I will remember ibus-hangul. Korean text input has been a struggle since 14.04. I will visit the korean ubuntu community. &#44048;&#49324;&#54633;&#45768;&#45796;.

---

