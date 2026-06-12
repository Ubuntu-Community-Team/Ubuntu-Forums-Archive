---
title: "Compiz Repositories broken! help..."
date: 2006-09-26
forum: General Help
---

### Post by des4ij on 2006-09-26
hey... i m trying to install xgl+compiz... i have compiz-core 13.38 but need 13.54 to install it with xgl and apparently the repositories at compiz (since they are moving rite now) have only version 38... if anyone has a backup of version 54 of compiz-core package can they plz post it up here... thx...

---

### Post by beerorkid on 2006-09-26
I have 13.53 and 13.57 if you need.

---

### Post by testube_babies on 2006-09-26
I think the only place that has quinn's compiz anymore is [http://beerorkid.com/compiz/](http://beerorkid.com/compiz/)

---

### Post by beerorkid on 2006-09-26
yeah I guess so.  i thought they got removed, but I logged in to the repo and it looks like it is all there.  I do not do anything with that repo, Quinn does all the magic.
Nice.

---

### Post by des4ij on 2006-09-26
hey but the latest version of compiz-core they have is 13.38 and i need 13.54 to install compiz-plugins... :-(

---

### Post by des4ij on 2006-09-26
hey beerorkid can u send me the compiz-core 13.57 package... thx man...

---

### Post by beerorkid on 2006-09-26
[http://beerorkid.com/tempcompizpkg/](http://beerorkid.com/tempcompizpkg/)

---

### Post by des4ij on 2006-10-02
hey beer or kid but how can install with those installation files... cuz when i try to install compiz-pluings it tells me csm is a dependency and when i try to install csm first then it tells me cannot install compiz-plugins.. is there a way i can add that site as a reposiory???... thx man..

---

### Post by beerorkid on 2006-10-02
> **des4ij said:**
> hey beer or kid but how can install with those installation files... cuz when i try to install compiz-pluings it tells me csm is a dependency and when i try to install csm first then it tells me cannot install compiz-plugins.. is there a way i can add that site as a reposiory???... thx man..

the bleeding edge compiz is no more.  it is now beryl.

this is a nice howto: [http://ubuntuforums.org/showthread.php?t=268036](http://ubuntuforums.org/showthread.php?t=268036)

iffin you have most of the compiz setup or going just do this:
```
sudo apt-get install beryl emerald emerald-themes
```
and it should be good to go.

You can just log into a regular metacity session and run ```
beryl-manager
``` to invoke beryl.

alternatativly you can put beryl-manager in system --> preferences --> sessions --> startup and make a new start up there.

You will now have :"BSM", not csm, and an icon for beryl in your notifications area where you can switch back and forth.

Good luck and if you have any Q's post them in the proper thread.

---

### Post by des4ij on 2006-10-02
thx... got it working nice and neat with beryl... just a question u know how compiz had the Applications, Places, and System menus on the tray have a splash effect... how can i do that for beryl... not a big deal if u dont know  becuz i got most of it workin... except for the water effect which i googled that my vid card doesnt support it... giving me this error:  GL_ARB_fragment_program is missing ... thx though...

---

### Post by beerorkid on 2006-10-02
> **des4ij said:**
> thx... got it working nice and neat with beryl... just a question u know how compiz had the Applications, Places, and System menus on the tray have a splash effect... how can i do that for beryl... not a big deal if u dont know  becuz i got most of it workin... except for the water effect which i googled that my vid card doesnt support it... giving me this error:  GL_ARB_fragment_program is missing ... thx though...

Originally Posted by djRobbieF  View Post
Woohoo! Another lover of the wobbly!

Beryl Settings Manager --> Wobbly Windows --> Map Window Types

Turn on PopupMenu, Unknown and DropdownMenu

---

### Post by des4ij on 2006-10-02
awesome... thx yo... its like WOAH... screw MICROSHIT... vista was slow on my laptop and didnt support anything... thx once again beerorkid... may thee obtain immortality... ;)

---

