---
title: "Installing Mono for C#"
date: 2016-04-02
forum: General Help
---

### Post by Stan58 on 2016-04-02
Hi I have tried to install MONO by "Xamarin" on to my system which is running Ubuntu 15.10. My first attempt was via the "Ubuntu Software Centre" which failed. So I tried directly from the MONO web site which also failed. So I tried to un-install the software but it now returns the following error message:   
 
[B]"This error could be caused by required additional software packages which are missing or not installable.
 Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time."[/B]

How can I resolve this issue and install the MONO software.

Regards
Stan

---

### Post by QIII on 2016-04-02
Hello!

You have only given us part of the story.  We do not yet know what "this error" is.

Would you please post the entirety of what is returned?  It may be long, so please enclose it in code tags:


1. If you are using the "Reply to Thread" button - highlight text and use the # button in the text box header.  Alternatively, click the # button first, place your cursor between the code tags and type or paste your text.

2. If using "Quick Reply" then type [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.  The square brackets are required.

---

### Post by Stan58 on 2016-04-03
```

Addition to    	 	 	 	   "This error could be caused by required additional software packages which are missing or not installable. 
Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time."

in the details is:
  	 	 	 	   
The following packages have unmet dependencies:

 
 
 libmono-system-configuration4.0-cil: libmono-system-data4.0-cil: libmono-system-web4.0-cil: mono-runtime: Depends: mono-runtime-sgen (= 4.2.3.4-0xamarin2) but 4.2.3.4-0xamarin2 is to be installed
 monodoc-manual:  

  
Hope I have replied correctly
Stan

  

```

---

