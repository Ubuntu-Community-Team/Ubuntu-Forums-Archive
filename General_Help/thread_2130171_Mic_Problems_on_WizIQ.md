---
title: "Mic Problems on WizIQ"
date: 2013-03-28
forum: General Help
---

### Post by Liaqat Qazi on 2013-03-28
I am unable to use my mic on WizIQ. When I try to acess microphone, the flash window comes up to ask for permission, but it is not responsive. No matter how many times you click on it it is doing nothing. Sound works in SKYPE. I am using Ubuntu 12.10 on a Lenovo Thinkpad R61.

---

### Post by gordintoronto on 2013-03-28
Did you install the "restricted extras"? How did you install WiziQ?

---

### Post by rsjtester on 2013-03-29
[ATTACH=CONFIG]240671[/ATTACH][ATTACH=CONFIG]240672[/ATTACH][ATTACH=CONFIG]240673[/ATTACH]

> **Liaqat Qazi said:**
> I am unable to use my mic on WizIQ. When I  try to access microphone, the flash window comes up to ask for  permission, but it is not responsive. No matter how many times you click  on it it is doing nothing. Sound works in SKYPE. I am using Ubuntu  12.10 on a Lenovo Thinkpad R61.


     [**[COLOR=#000000]@ Liaqat Qazi[/COLOR]**]("http://ubuntuforums.org/member.php?u=1804743")      
[SIZE=5]**This is not WizIQ's issue**[/SIZE], it's  Adobe Flash player's issue on Ubuntu OS , it will happen on any flash  based application which seeks access to your mic and camera devices. 

**WizIQ can provide you solution**.Following is the solution.



[LIST=1]
[*]Write 'adobe' in your ubuntu desktop search bar.
[*]Adobe flash player app will be listed.
[*] open it.
[*]click on Camera and Mic tab.
[*]Click on 'Camera and Microphone settings by site' button
[*]A window appears.
[*]If under Website column authorlive.wiziq.com is not added  then add it by clciking on the 'ADD' button. Add authorlive.wiziq.com in  the 'website domain' text box and select 'Allow' in the drop down under  the text box.
[*]If authorlive.wiziq.com is already added then click in  column 'Camera and mic access' (in front of the authorlive.wiziq.com  entry) and choose/set Allow. then clsoe teh window.
[*]Now when you open session Flash will not ask you to allow.
[/LIST]

See attached 'ubuntu screenshots' for details.


Hope it helped you.:smile::razz:

---

