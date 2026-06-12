---
title: "administration tools not loading. and i cant unlock network settings"
date: 2008-06-23
forum: General Help
---

### Post by punkrocker07 on 2008-06-23
ok so heres the thing. im new to linux and i have ubuntu 8.04 hardy. 

When i try to unlock my network settings it starts but then dosnt open up admin so i cant put my password in and unlock it. 


i tried to upgrade using sudo and it didnt fix the problume.

alot of the admin programs dont work. i made sure that i am a Administrator.
](*,) 

any help would be vary appersiated.

TY

---

### Post by Mosgjig on 2008-08-03
Has this been resolved?

When I initially installed 8.04, I was able to setup my wireless for one router, however after a week and a change in location I need to add another wireless configuration and am unable to edit any network settings.  When I click unlock I get an error message.

---

### Post by zvacet on 2008-08-03
@ **Mosgjig**

When you type sudo and press enter do yo get any errors?

---

### Post by rEbyTer on 2008-08-03
Go to System > Settings > Authorizations and find 
 org.freedesktop.systemtoolsbackends. **Manage system configuration**.
Use edit button and just put yes to everything and then ok.

Tell me if works.
I don't know if it is a[COLOR="Red"] safe hack[/COLOR] but you could try this. everytime you'll go to network manager you will **[COLOR="Red"]not[/COLOR]** be asking for that password so be careful at this stage, maybe you don't want someone to screw your network settings.

---

