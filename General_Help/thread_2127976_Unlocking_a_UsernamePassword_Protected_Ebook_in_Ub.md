---
title: "Unlocking a Username/Password Protected Ebook in Ubuntu 12.04LTS"
date: 2013-03-21
forum: General Help
---

### Post by FenrirXIII on 2013-03-21
**Dilemma**

     Some colleges or universities provide ebooks (in .pdf formats) to student for free. These ebooks usually require a student login and password to unlock the ebook's content. The default pdf viewer installed in Ubuntu 12.04LTS is unable to unlock them.
 

 **Solution:**

     **STEP 1: Install Adobe Acrobat Reader 9+**

 
[LIST]
[*]Open TERMINAL 
[/LIST]
              [TABLE="width: 569"]
[TR]
[TD="width: 559"]                         *sudo add-apt-repository “deb                         [http://archive.canonical.com/](http://archive.canonical.com/) precise partner”*
                         *sudo apt-get update*
                         *sudo apt-get install acroread*[/TD]
[/TR]
[/TABLE]
          **    STEP 2: Trial and Error**
 
[LIST]
[*]Open Acrobat Reader via _Dash Home_ 
[*]Open desire file
[LIST]
[*]Prompt for your student username and password
[LIST]
[*]refer to your school if necessary 
[/LIST]
      
  
[/LIST]
    
[/LIST]
   [B]    There are two things that can happen here:
[/B]
**        [COLOR=#0000cd]1. Everything works perfectly[/COLOR]**

[COLOR=#ff0000]**        2. "Your security settings don't allow access to the protectedpdf server. You must allow                 access to the server.”**[/COLOR]

 

     **STEP 3: Allowing access to the protectedpdf server.**

 
[LIST]
[*]_In Acrobat Reader_
[LIST]
[*]Go to Edit > Preferences
[LIST]
[*]choose Trust Manager on the left 
[*]select Change Settings on Internet Access from PDF
[LIST]
[*]change the allow access to allow all 
[/LIST]
         
 
  
[/LIST]
        
[/LIST]
   
[/LIST]
   _***You are now able to view you ebook and its content in Ubuntu after logging in your school student username and password. Enjoy.***_

---

### Post by zexsuik on 2013-04-13
Thank you! You're awesome.

---

