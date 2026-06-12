---
title: "How Firefox to distinguish current tab ?"
date: 2020-11-12
forum: General Help
---

### Post by petrogromovo on 2020-11-12
Hello,
Having Firefox 81.0.2 under Kubuntu 18 I have a problem
that it is difficult to see to distinguish current tab:
[https://prnt.sc/vhzv8m](https://prnt.sc/vhzv8m)

Also I would like to set bigger default font size for it and I found fonts options
but setting big value it did not help me...

How can I do it?

Thanks!

---

### Post by tea for one on 2020-11-12
To distinguish the current tab, you could have a look at Theme Addons for Firefox.

[https://addons.mozilla.org/en-GB/firefox/addon/game-red-with-highlighted-tab/?utm_source=addons.mozilla.org&utm_medium=referral&utm_content=search](https://addons.mozilla.org/en-GB/firefox/addon/game-red-with-highlighted-tab/?utm_source=addons.mozilla.org&utm_medium=referral&utm_content=search)

It certainly highlights the open tab but it's quite flamboyant.

There are probably others more suitable if you spend some time searching.

---

### Post by Holger_Gehrke on 2020-11-12
The user interface of Firefox can be styled using CSS in a file named userChrome.css in a directory named 'chrome' inside your profile directory (this has nothing to do with the Google branded browser named Chrome; the name is much older than that and just used to mean 'stuff to make it look better but with no real function', similar to chrome on old cars).

Putting this
```

@namespace url("http://www.mozilla.org/keymaster/gatekeeper/there.is.only.xul");

/* Active Tab in bold */
tab.tabbrowser-tab hbox.tab-content[selected=true] {
  font-weight: bold
}

```
in a userChrome.css will make the title of the active tab bold. You might have to create the directory 'chrome'. In case you don't know: your Firefox profile directory is in '$HOME/.mozilla/firefox/' and it's name is a random string followed by a dot and the name of the profile (.default for the default profile).

Holger

---

### Post by walts48 on 2020-11-13
> **petrogromovo said:**
> Hello,
Having Firefox 81.0.2 under Kubuntu 18 I have a problem
that it is difficult to see to distinguish current tab:
[https://prnt.sc/vhzv8m](https://prnt.sc/vhzv8m)

Thanks!

Have you tried out the Dark theme?

Menu button > Add-ons > Themes.

---

### Post by petrogromovo on 2020-11-14
I create a new file as 
[/home/user/.mozilla/firefox/jmh54t5x.default/userChrome.css]("file:///home/serge/.mozilla/firefox/jmh54t5x.default/userChrome.css")
with lines were proposed :
> @namespace url("http://www.mozilla.org/keymaster/gatekeeper/there.is.only.xul");

/* Active Tab in bold */
tab.tabbrowser-tab hbox.tab-content[selected=true] {
  font-weight: bold
  text-decoration: underline;
}

but it did help, I do not see these classes are applied at the current tab of Firefox.

I found a way how to Change theme at about:addons, but a way with  browser styles you proposed seems better.

2)Why I can not to set font bigger at about:preferences ? In my printscreen I show how 
I set default size, but it does not applied.

---

