---
title: "Firefox CTD after java howto installation."
date: 2004-11-11
forum: General Help
---

### Post by HiddenWolf on 2004-11-11
I did the add java to firefox howto. Installed java.

Now when I try to go to my banking page. ([www.postbank.nl](www.postbank.nl)) and go to the java-login part of the site, firefox crashes to desktop.

How can I fix this?

---

### Post by ashley_v on 2004-11-11
[QUOTE=][/QUOTE]
 In /usr/local/j2re1.4.2_05/plugin/i386/ there 3 versions of the java plugin there.  I have not installed java in a while and the how-to on this site seems pretty staright forward except that you must link the appropriate libjavaplugin.so file with your correct version of gcc.


If you link the wrong one it will not work or maybe even crash.  So double check that and see if you did.  Also you don't have to use the firefox from the apt repository if your even using that one.  Download the newer one from mozilla.org and extract it in your home directory and try the java plugin with that.

---

### Post by adbak on 2004-11-11
I made the mistake of downloading JRE 1.5.  I found out that if you make a symlink to /home/username/.mozilla/plugins, it'll crash the browser.  You have to use the J2RE 1.4.2.

I don't know if that helps you, but it helped me.

---

### Post by pgferro on 2004-11-14
I installed java succesfully (I can use azureus and other java programs) but with 1.4 and firefox 1.0 following the instructions, the browser crashes everytime there is a java page. Tried the 3 plugins in the java plugins directory : ns610 and ns610-gcc crash, ns4 no plugin installed.

Any ideas ?

Thanks

--
PG

---

### Post by HiddenWolf on 2004-11-14
I have got exactly the same problem.

---

### Post by scoon on 2004-11-15
[QUOTE=pgferro]I installed java succesfully (I can use azureus and other java programs) but with 1.4 and firefox 1.0 following the instructions, the browser crashes everytime there is a java page. Tried the 3 plugins in the java plugins directory : ns610 and ns610-gcc crash, ns4 no plugin installed.

Any ideas ?

Thanks

--
PG[/QUOTE]

Hey there, 

Try 1.5.  I use it with no problems what so ever.

scoon

---

### Post by HiddenWolf on 2004-11-16
No luck so far. It's stil crashing on me.

---

### Post by pgferro on 2004-11-16
Same here.... (with 1.5)

---

