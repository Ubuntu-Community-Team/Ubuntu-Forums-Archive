---
title: "Kubuntu ignores LC_ALL settings"
date: 2007-09-14
forum: General Help
---

### Post by Ran.Rutenberg on 2007-09-14
Hi,

When I use LC_ALL=he_IL to launch something in Hebrew it just doesn't work if my language setting in the system settings dialog is set to English and vice-versa: if the language is set to Hebrew I can't use LC_ALL=en_US to start programs in English.
I tried to search the internet for an answer but I didn't find anything.

my locale -a output is:
```
C
ca_ES.utf8@valencia
ca_ES@valencia
en_AU
en_AU.utf8
en_BW
en_BW.utf8
en_CA
en_CA.utf8
en_DK
en_DK.utf8
en_GB
en_GB.iso885915
en_GB.utf8
en_HK
en_HK.utf8
en_IE
en_IE@euro
en_IE.utf8
en_IN
en_NZ
en_NZ.utf8
en_PH
en_PH.utf8
en_SG
en_SG.utf8
en_US
en_US.iso885915
en_US.utf8
en_ZA
en_ZA.utf8
en_ZW
en_ZW.utf8
he_IL
he_IL.uft8
he_IL.utf8
POSIX

```

Sincerely,
Ran Rutenberg

---

### Post by debianchick on 2007-09-14
> **Ran.Rutenberg said:**
> Hi,

When I use LC_ALL=he_IL to launch something in Hebrew it just doesn't work if my language setting in the system settings dialog is set to English and vice-versa: if the language is set to Hebrew I can't use LC_ALL=en_US to start programs in English.
I tried to search the internet for an answer but I didn't find anything.

my locale -a output is:
```
C
ca_ES.utf8@valencia
ca_ES@valencia
en_AU
en_AU.utf8
en_BW
en_BW.utf8
en_CA
en_CA.utf8
en_DK
en_DK.utf8
en_GB
en_GB.iso885915
en_GB.utf8
en_HK
en_HK.utf8
en_IE
en_IE@euro
en_IE.utf8
en_IN
en_NZ
en_NZ.utf8
en_PH
en_PH.utf8
en_SG
en_SG.utf8
en_US
en_US.iso885915
en_US.utf8
en_ZA
en_ZA.utf8
en_ZW
en_ZW.utf8
he_IL
he_IL.uft8
he_IL.utf8
POSIX

```Sincerely,
Ran Rutenberg

Undo what you have done than try this Wiki [U][**[SIZE=3]HebrewLocalizationHowto[/SIZE]**]("https://help.ubuntu.com/community/HebrewLocalizationHowto")





[/U]

---

### Post by Ran.Rutenberg on 2007-09-14
> **debianchick said:**
> Undo what you have done than try this Wiki [U][**[SIZE=3]HebrewLocalizationHowto[/SIZE]**]("https://help.ubuntu.com/community/HebrewLocalizationHowto")





[/U]

I've done all the things described in this Howto before and it didn't help. I have Hebrew installed on my machine. The thing is that if Kubuntu's language is English I can't launch a program in Hebrew. If Kubuntu's language is Hebrew all the programs are in Hebrew as well even if I use LC_ALL=en_US.

---

### Post by Ran.Rutenberg on 2007-09-18
Anyone? Please

---

