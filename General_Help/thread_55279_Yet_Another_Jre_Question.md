---
title: "Yet Another Jre Question"
date: 2005-08-08
forum: General Help
---

### Post by mcrofutt on 2005-08-08
I've installed java runtime enviroment via synaptic,,, STULL no java plugins found in Firefox ver. 1.06. This took an hour and a half to d/l on my dial-up connection. Please tell me it wasn't a waste of time, and step-by-step me how to get Firefox to recognize it!!!! PLEASE somebody! ](*,) 

 THANKS in advance!!!! \\:D/ 
 Mark

---

### Post by roland on 2005-08-08
[QUOTE=mcrofutt]I've installed java runtime enviroment via synaptic,,, STULL no java plugins found in Firefox ver. 1.06. This took an hour and a half to d/l on my dial-up connection. Please tell me it wasn't a waste of time, and step-by-step me how to get Firefox to recognize it!!!! PLEASE somebody! ](*,) 

 THANKS in advance!!!! \\:D/ 
 Mark[/QUOTE]

This is done in the following way (so it was no waste of time downloading Java :)).

Check where you have Java installed, using a root terminal (start with Applications - System Tools - Root Terminal). I assume it is installed in the directory [font=courier]/usr/local/java/jre1.5.0_02[/font] or something similar. Try to check the actual name of that directory by typing [font=courier]ls /usr/local/java[/font].

You have to type the following two commands one after another in the root terminal. I have used jre1.5.0_02 as the install dir, please substitute it with the name applicable for your computer.

```

ln -sf /usr/lib/j2sdk1.5-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so /etc/alternatives/firefox-javaplugin.so
ln -sf /etc/alternatives/firefox-javaplugin.so /usr/lib/mozilla-firefox/plugins/libjavaplugin_oji.so

```

Now restart Firefox, and Java should work. If not, please notify me.

---

### Post by mcrofutt on 2005-08-08
\\:D/  \\:D/  \\:D/  \\:D/  \\:D/  :)  :)  :) 
 MY HERO!!!!!!!
 Got it going just like that!!
 AND I got to do something I'd never done before! Never had made a sym-link before that,,,lol
 THANKS A MILLION!!!!!!!!
  Mark
 
 The only thing I know FOR SURE,,,,,,,,Is ,,, I don't know ANYTHING.

---

### Post by roland on 2005-08-09
[QUOTE=mcrofutt]
 MY HERO!!!!!!!
 Got it going just like that!!
 AND I got to do something I'd never done before! Never had made a sym-link before that,,,lol
 THANKS A MILLION!!!!!!!!
  Mark
 
 The only thing I know FOR SURE,,,,,,,,Is ,,, I don't know ANYTHING.[/QUOTE]

My pleasure to help. I tried Java in Firefox after reading your post, and only by then I realized that it didn't work. Then I tried to search this forum, there has been talked about it, but you need to plough through lots of posts before finding the answer. Eventually I found this by using google's fifth hit or so, and put it here in a short way. So you helped me out as well by asking this question, because it works now for me too ;)

And please don't degrade yourself, everyone starts by knowing nothing at all when using Linux :P

---

### Post by rjwood on 2005-08-11
[QUOTE=roland]This is done in the following way (so it was no waste of time downloading Java :)).

Check where you have Java installed, using a root terminal (start with Applications - System Tools - Root Terminal). I assume it is installed in the directory [font=courier]/usr/local/java/jre1.5.0_02[/font] or something similar. Try to check the actual name of that directory by typing [font=courier]ls /usr/local/java[/font].

You have to type the following two commands one after another in the root terminal. I have used jre1.5.0_02 as the install dir, please substitute it with the name applicable for your computer.

```

ln -sf /usr/lib/j2sdk1.5-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so /etc/alternatives/firefox-javaplugin.so
ln -sf /etc/alternatives/firefox-javaplugin.so /usr/lib/mozilla-firefox/plugins/libjavaplugin_oji.so

```

Now restart Firefox, and Java should work. If not, please notify me.[/QUOTE]
 can you help with this??
XML Parsing Error: no element found
Location: jar:resource:///chrome/toolkit.jar!/content/mozapps/update/updates.xml
Line Number 1, Column 1:
Error: uncaught exception: [Exception... "Component returned failure code: 0x80570009 (NS_ERROR_XPC_BAD_CONVERT_JS) [nsIXPCComponents.lookupMethod]"  nsresult: "0x80570009 (NS_ERROR_XPC_BAD_CONVERT_JS)"  location: "JS frame :: chrome://global/content/XPCNativeWrapper.js :: anonymous :: line 91"  data: no]
thanks!!!

---

### Post by roland on 2005-08-11
Maybe I can if you tell me how to reproduce this error.

---

### Post by rjwood on 2005-08-11
[QUOTE=roland]Maybe I can if you tell me how to reproduce this error.[/QUOTE]
 I am not sure. this was taken off firefox tools menu for java script console. My java toolkit does not work either but, I am not having any problems with web pages or card playing on yahoo. I think java is needed for that--isnt it? As you can probably tell, I am not very computer educated.  thank you for the help!!

---

### Post by roland on 2005-08-11
The yahoo games need Java indeed. I wouldn't be worried so much about the errors given in the Javascript console, because they are generated by errors on the page you are viewing, not by Javascript on your computer. Also note that Java and Javascript are two very different things: Java is meant for small applications (called "applets"), such as a Yahoo! game. Javascript is designed as an easy programming language for enhancements on a webpage, such as small menus and actually the "quick reply" button on this forum.

---

### Post by rjwood on 2005-08-11
[QUOTE=roland]The yahoo games need Java indeed. I wouldn't be worried so much about the errors given in the Javascript console, because they are generated by errors on the page you are viewing, not by Javascript on your computer. Also note that Java and Javascript are two very different things: Java is meant for small applications (called "applets"), such as a Yahoo! game. Javascript is designed as an easy programming language for enhancements on a webpage, such as small menus and actually the "quick reply" button on this forum.[/QUOTE]
 Thank You for the info and for easing my concerns. Have a great Day!

p.s. You won't believe this but, I went ahead and did your change in root terminal and now java-script will not work ie.  play cards in yahoo. I guess I didn't need to make that change that you sugested to the other person. So :neutral: is there any way to fix it?? :grin:

---

