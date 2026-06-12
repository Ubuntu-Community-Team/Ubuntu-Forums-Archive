---
title: "can I run this userscript with Firefox using a bash script?"
date: 2021-03-05
forum: General Help
---

### Post by ardouronerous on 2021-03-05
Firefox's recent update, FF86, changed the browser's search behavior, in the past, all you had to do was type a search query on the address bar and click  on Wikipedia, and that's it, it takes you to the Wikipedia article, but with FF86, you have to use shift+click Wikipedia or press enter after  clicking on Wikipedia, which is slower and inconvenient. A one click  search is much more faster and this userscript is suppose to return this functionality to FF86.

Here's the instructions on how to use this userscript with Firefox: [https://www.reddit.com/r/firefox/comments/ls0ffy/oneoffsrefresh_redux_single_click_search_icons_in/](https://www.reddit.com/r/firefox/comments/ls0ffy/oneoffsrefresh_redux_single_click_search_icons_in/)

The problem though is that in order to use this userscript, I have add files in Firefox's install directory and in order to do that, I have to have root access and I don't feel comfortable with that.

So, is there a way to use this userscript without giving root access, like put the necessary files somewhere in my Home directory and instruct Firefox to use this userscript using a batch script that I can insert in Firefox's desktop executable?

Thanks.

---

### Post by mikewhatever on 2021-03-06
I don't think you can use javascript as bashscript. You could have Firefox downloaded directly from firefox.com, and installed locally in a home folder. That would not require "root access", but you'll need to create menu launchers manually, or launch it from the installed folder.

---

### Post by ardouronerous on 2021-03-06
> **mikewhatever said:**
> I don't think you can use javascript as bashscript. You could have Firefox downloaded directly from firefox.com, and installed locally in a home folder. That would not require "root access", but you'll need to create menu launchers manually, or launch it from the installed folder.

That would require me to manually update Firefox.

Can I use this userscript with the flatpak version of Firefox then? I have a startup script that checks for flatpak updates every time I boot into my computer.

---

### Post by CelticWarrior on 2021-03-06
> [COLOR=#000000]That would require me to manually update Firefox.[/COLOR]

The "self-contained" Firefox updates automatically but independently of the system.
(i.e., it behaves like in Windows)

---

### Post by ardouronerous on 2021-03-07
> **mikewhatever said:**
> I don't think you can use javascript as bashscript. You could have Firefox downloaded directly from firefox.com, and installed locally in a home folder. That would not require "root access", but you'll need to create menu launchers manually, or launch it from the installed folder.

Thanks that worked and I'm able to run the js files.

> **CelticWarrior said:**
> The "self-contained" Firefox updates automatically but independently of the system.
(i.e., it behaves like in Windows)

Since this is my first time running Firefox in this manner, does Firefox update itself automatically when I startup the browser or do I have to always go "Open menu -> Help -> About Firefox" to initiate the update?

Also, are there any security concerns in using Firefox in this manner, from the Home folder?

---

### Post by CelticWarrior on 2021-03-07
> **ardouronerous said:**
> Since this is my first time running Firefox in this manner, does Firefox update itself automatically when I startup the browser or do I have to always go "Open menu -> Help -> About Firefox" to initiate the update?

Also, are there any security concerns in using Firefox in this manner, from the Home folder?

It updates itself automatically and will show a green dot overlay in the "hamburger" menu. When you click the menu it will say restart Firefox to install updates. 
There should be no difference regarding security when using the same version.

---

### Post by ardouronerous on 2021-03-07
> **CelticWarrior said:**
> It updates itself automatically and will show a green dot overlay in the "hamburger" menu. When you click the menu it will say restart Firefox to install updates. 
There should be no difference regarding security when using the same version.

Thanks.

---

