---
title: "firefox doesn't work properly after latest update"
date: 2006-10-03
forum: General Help
---

### Post by Charlotte on 2006-10-03
Hallo over there,

after doing the latest security updates this afternoon, firefox seems not to work properly anymore. Konqueror did not start, too - but this obviously could be remedied after installing the thunderbird packages retained. (??)

Firefox started with missing locales (minor problem) but also there were extensions disabled (calendar) or missing (noscript, customizegoogle) or outdated and not updateable (adblock). I went through the update/install procedure repeatedly only to see the message (xx will be installed after restarting firefox) and after restarting nothing has changed.

I greatly would appreciate some hints. Thanks in advance.

I am surfing the net with Opera 9.02 momentarely - even that programme seems a bit malfunctioning and I couldn't make sense of what's going on on my machine.


Regards,
Charlotte

---

### Post by Charlotte on 2006-10-03
> **Charlotte said:**
> 

I am surfing the net with Opera 9.02 momentarely - even that programme seems a bit malfunctioning and I couldn't make sense of what's going on on my machine.


Sorry - I have to correct myself. Opera is running properly. 

Regards,
Charlotte

---

### Post by moore.bryan on 2006-10-03
[COLOR=black]*you could try [swiftfox]("http://getswiftfox.com") or [firefox2.0rc1]("http://www.mozilla.org/projects/bonecho/all-rc.html") and see if they work... with which ff are you currently having problems?*
[/COLOR]

---

### Post by Charlotte on 2006-10-03
Hallo, Bryan,

thank you so much for answering and the hints!

Fumbling around with the config files in my home dir I figured out that obviously my firefox profile was damaged. I could create a new one by calling in Firefox with "firefox -profileManager". All went ok and I was able to install the extensions I wanted afterwards.  

BTW: Firefox 2.0 RC1 I tested before crying for help here - no hope. Maybe it wants to use the old crashed profile...


Have fun,
Charlotte

---

### Post by moore.bryan on 2006-10-03
*i'm glad you figured it out... testing those other programs would have let me know if it was your profile.  how did that get flubbed?  anyways, glad you figured it out!*

---

### Post by Kilz on 2006-10-04
> **moore.bryan said:**
> [COLOR=black]*you could try [swiftfox]("http://getswiftfox.com") or [firefox2.0rc1]("http://www.mozilla.org/projects/bonecho/all-rc.html") and see if they work... with which ff are you currently having problems?*
[/COLOR]

Swiftfox is non free software. I wound not recommend anyone who loved FOSS to use it. It is licensed under its own license that restricts redistribution. One of the 4 main freedoms.

---

### Post by moore.bryan on 2006-10-04
> **Kilz said:**
> Swiftfox is non free software. I wound not recommend anyone who loved FOSS to use it. It is licensed under its own license that restricts redistribution. One of the 4 main freedoms.
*although technically true, i think calling it non-free is taking foss a little too literally.  in the "spirit" of the rules, i think it still fits because the source is available for anyone who wants to tinker with it.  from the licence page on the swiftfox [website]("http://www.getswiftfox.com/LICENSE"):> These license restrictions are in place to protect   the integrity of Swiftfox and to ensure that when users of the community download and install Swiftfox   they can be assured they are getting an official   build that has not been altered in anyway that might   include malicious content.now, i totally agree that can be interpreted as closed, i'm just not sure it's completely against foss... good points, though, kilz...*

---

### Post by Kilz on 2006-10-04
> **moore.bryan said:**
> *although technically true, i think calling it non-free is taking foss a little too literally.  in the "spirit" of the rules, i think it still fits because the source is available for anyone who wants to tinker with it.  from the licence page on the swiftfox [website]("http://www.getswiftfox.com/LICENSE"):now, i totally agree that can be interpreted as closed, i'm just not sure it's completely against foss... good points, though, kilz...*

I dont think its worth whats lost for whats gained. Let me explain what I mean by that. Swiftfox bacicly is Firefox thats compiled by someone. Things are disabled to make it start faster. The person who compiles it changes the name and the logo and then changes the license.
So for the new name and logo he takes away a freedom from you. He doesnt add anything like say Flock does (but they release under the gpl anyway). Maybe I would change my mind a little if there was some feature was added that isnt in firefox. But there isnt, if anything there is less. [Dont try and run Swiftfox in languages other that English.]("http://www.ubuntuforums.org/showpost.php?p=1370053&postcount=3")
You may say well what do I lose. You lose because Distro's like Ubuntu cant package it and add it to the repos. People cant modify the settings and change it a little to make it better. Then give it to a friend. Things you can do with Firefox.
The compiler says its for your safety. But who is he that we should trust him over someone else? He is just taking the Firefox code and compiling it. Does that make him more trustworthy?

---

### Post by moore.bryan on 2006-10-04
*once again, good points kilz... i had never heard of flock; pretty interesting idea.  i guess i interpret the speed increases as features "added" to swiftfox, but it's true the changes which make it faster is more about exclusion than inclusion.  so your issue with swiftfox relies more on it being a repackaged firefox with new license/logo/name than it's inner workings?*

---

### Post by Kilz on 2006-10-04
> **moore.bryan said:**
> *once again, good points kilz... i had never heard of flock; pretty interesting idea.  i guess i interpret the speed increases as features "added" to swiftfox, but it's true the changes which make it faster is more about exclusion than inclusion.  so your issue with swiftfox relies more on it being a repackaged firefox with new license/logo/name than it's inner workings?*

That and it cant be redistributed. 
First off , there are no diffrences in its inner workings. Firefox is free and can do everything Swiftfox can. The increesed speed is only humanly noticable at startup to most people. Is 1 second worth giving up on freedom.
Second Redistribution. The freedom of redistribution isnt one that I alone hold. The Free Software Foundation has a [good deffinition of Free]("http://www.gnu.org/philosophy/free-sw.html") as in freedom software. I agree with it. 
Now dont think Im some zealot. Im not. If there is a good reason for using a non free application. Say an important feature isnt avilable in the free version I would use the non free one. An example of this is ATI drivers. I have to use the non free ones if I want 3d acceleration. The non free ones dont have it at all.
But I have written to ati and told them as a customer that it would be better imho if they released the driver. If a free one becomes avilable that has 3d acceleration I will remove the non free one.
But is 1 second faster starting worth limiting freedom? Is it worth sending the "its ok to limit others" signal to the person compiling Swiftfox for 1 second faster starts? To me, no its not worth it.

---

