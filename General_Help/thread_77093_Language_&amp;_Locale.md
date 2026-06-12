---
title: "Language &amp; Locale"
date: 2005-10-16
forum: General Help
---

### Post by krojc on 2005-10-16
Ok, first of all, everything works!
If I use my native language and native locale, everything is perfect. The same if I use English interface and english locale. The thing gets complicated when I want to use english interface with native locale and keyboard support.

Native locale works in X and also interface is english for the packages I have no native language *.mo files, but since I translate linux apps I have some in my native language for testing and all those apps always start in my language and not english.

What is worse is, that console never produced any special signs of my language, except when the whole system is in my language.

I really worked for weeks on this problem and all I come up with was, that this settings are not on one position, but you have to set a gazillion files for just a simple language tweak. Last thing that I did wrong was using Language selector to set my files and now I can not set it back from my native language even thou I ALWAYS log in as default POSIX English.

So.. please can write down ALL the freaking files I need to manually edit to set one language on the interface and one on locale and keyboard support in X and console.

Thanks this is much apreciated...
Matej

---

### Post by krojc on 2005-10-19
Anyone, please...
I'm not reinstalling!

---

### Post by NiN on 2005-10-20
Hi!

Hope I understod you correctly.
If you simply want to start an application with your preferred language in an "C" environment, I´d suggest starting a terminal and modify the environment variables in that specific terminal.

that way you have all normal apps in english and only the ones started from the terminal in your language.

(you need to export LANG, LANGUAGE, LC_ALL).

Hope that helps ;)

---

### Post by bdash on 2005-10-20
I don't think you need special locales if you want a system in English. All you want is to input in your language, right? Ubuntu being UTF8 you should be able to input in any language whatever your locale is.

---

### Post by krojc on 2005-10-22
Thanks guys!

I did crack it :), yesterday. The thing was, that all settings colided with each other from linux, Gnome and kde. After removing all entries it worked like it should. I think this was upgrade problem from hoary to breezy and some settings got mixed up.

Thanks again for answer.

---

