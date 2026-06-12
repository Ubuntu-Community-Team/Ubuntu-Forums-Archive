---
title: "What's going on with Firefox 1.0.4?"
date: 2005-06-12
forum: General Help
---

### Post by j_baer on 2005-06-12
Why isn't firefox 1.0.4 available as a regular update? 

Although rumored to be available via a backport this is too important an app to send users down that road. It should be in universe as a core ubuntu app.

---

### Post by Takis on 2005-06-12
What do you mean?
Have you tried looking for the package 'mozilla-firefox' rather than 'firefox'? The version I can see through the standard repositories is 1.0.4.

---

### Post by FizDev on 2005-06-12
He means that even though it is there (as mozilla-firefox) it isn't the latest version. It's the 1.0.2 I thinks while they are now at 1.0.4 on their website.

---

### Post by Takis on 2005-06-12
Oh yeah forgot one backport repository :-\".

I see what you mean. My understanding though is that other than OS security updates, the Ubuntu team don't put up any updates till the next release. Pls keep in mind I might be wrong.

---

### Post by bored2k on 2005-06-12
Ubuntu's Firefox has all -or most- of the security updates already implemented. They did so before the 1.0.4 so basically you already have all security updates. Now if you're not sure and want the latest, backports supply them./

---

### Post by j_baer on 2005-06-13
I don't have a problem using version 1.0.2 but if you go to download a theme, the mozilla site blocks anything less than 1.0.4. {?}

Furthermore, there is a reference on the site to a bug where by the version number in a ubuntu backport package didn't get set correctly.

  ](*,) 

I realize this is **not** an ubuntu problem but the ubuntu user is placed in the middle of a finger pointing game.

My suggestion is _fix the bug_, place the package into the respository, and move on to more important issues.

This is an _unnecessary_ smear on an otherwise wonderful distro.

---

### Post by dresnu on 2005-06-13
[QUOTE=j_baer]I don't have a problem using version 1.0.2 but if you go to download a theme, the mozilla site blocks anything less than 1.0.4. {?}[/QUOTE]

Here's how to install themes without upgrading to 1.0.4

[http://www.ubuntuforums.org/showthread.php?t=35151&highlight=firefox+1.0.4+themes](http://www.ubuntuforums.org/showthread.php?t=35151&highlight=firefox+1.0.4+themes)

---

### Post by drummer on 2005-06-13
[QUOTE=j_baer]I don't have a problem using version 1.0.2 but if you go to download a theme, the mozilla site blocks anything less than 1.0.4. {?}

Furthermore, there is a reference on the site to a bug where by the version number in a ubuntu backport package didn't get set correctly.

  ](*,) 

I realize this is **not** an ubuntu problem but the ubuntu user is placed in the middle of a finger pointing game.

My suggestion is _fix the bug_, place the package into the respository, and move on to more important issues.

This is an _unnecessary_ smear on an otherwise wonderful distro.[/QUOTE]
 I had the problem where i couldn't download themes from the firefox site.. even _after_ upgrading to 1.0.4 from backports :(  so I installed using the package on the firefox site in /opt and all's working better (so far) and I can install themes :)
NB - I also changed the symlink pointing to firefox in /usr/bin to it's new location in /opt..

I wouldn't call it a smear as such.. it just makes setting up / configging linux more fun ;) ..and satisfying after overcoming problems.

---

### Post by j_baer on 2005-06-13
Thanks dresnu ...

This patched worked. Should be pinned or posted in the howto for any new users to ubuntu.


 :)

---

### Post by angrykeyboarder on 2005-06-13
[QUOTE=j_baer]I don't have a problem using version 1.0.2 but if you go to download a theme, the mozilla site blocks anything less than 1.0.4. {?}

Furthermore, there is a reference on the site to a bug where by the version number in a ubuntu backport package didn't get set correctly.

  ](*,) 

I realize this is **not** an ubuntu problem but the ubuntu user is placed in the middle of a finger pointing game.

My suggestion is _fix the bug_, place the package into the respository, and move on to more important issues.

This is an _unnecessary_ smear on an otherwise wonderful distro.[/QUOTE]

Dirty little secret....


 [http://archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox_1.0.4-1ubuntu3_i386.deb]("http://archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox_1.0.4-1ubuntu3_i386.deb")

---

