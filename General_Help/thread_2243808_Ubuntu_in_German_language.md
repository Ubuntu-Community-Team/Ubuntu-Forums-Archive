---
title: "Ubuntu in German language"
date: 2014-09-11
forum: General Help
---

### Post by Canaryguy on 2014-09-11
Hello,

I have Ubuntu x64 English version installed on my laptop. I wanted to change the language to German. I went to the application Languages and I installed the German language but after the installation it is not in the list of installed languages and I cannot set the system to German. Is this not available?

---

### Post by Cliff_Simonds on 2014-09-11
you need to move german by dragging and dropping to the very top bzw. english down, and don't forget to make appropiate changes in regional formats, next click the apply  system wide, then either logout-login or what I find always better reboot. As that I'm an american expat living in germany, I have both languages too, but english is my primary for system and deutsch is primary for LibreOffice.

---

### Post by Canaryguy on 2014-09-11
The problem is that I cannot drag and drop it because it is not in the list. The language is installed but it doesn't appear in the list. Very strange.

---

### Post by Cliff_Simonds on 2014-09-11
Does your screen look like this?
[ATTACH=CONFIG]256367[/ATTACH]
If not, how do you know that the german language pack was downloaded, Synaptic?

---

### Post by Canaryguy on 2014-09-11
Yes, it looks like exactly the same except that I don't habe "Deutsch (Deutschland" in the list. When I go to Install/Remove languages... I see that German is installed.

---

### Post by Cliff_Simonds on 2014-09-11
If the ubuntu downloaded it, and I'm very sure you'ld have noticed it(it takes what feels like forever), the only other thing I can think of right now is in user system settings>user accounts>your account> Language. If that doesn't work maybe someone else with more expierence can(at best with CLI Voodoo). Are you using Firefox and in Tools>add-ons>languages do you have the Deutsch language pack and how about in Libreoffice, when not I don't believe it was installed, Check in synaptic, downloaded isn't installed.

---

### Post by Canaryguy on 2014-09-11
It's really strange. Libreoffice detects the German language.
I even tried installing Spanish and after that I have the option to change the system to Spanish. I reinstalled German but changing the system to German is not possible.
As last resource I could reinstall Ubuntu.

---

### Post by Cliff_Simonds on 2014-09-11
If it can wait, you should wait a couple of days, don't forget this forum is world wide, and maybe someone else is just waking up that can help.

---

### Post by Canaryguy on 2014-09-11
Well, thanks anyway Cliff_Simonds for trying to help :-)

---

### Post by Canaryguy on 2014-09-19
I have found by chance the solución. Now it's all fixed.

sudo apt-get install --reinstall locales

sudo dpkg-reconfigure locales

---

### Post by Cliff_Simonds on 2014-09-19
Great that you found the answer, and even better that you posted it. hopefully it'll help others in the same predicament. So alles klar jetzt,Na?

---

