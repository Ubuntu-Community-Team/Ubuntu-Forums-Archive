---
title: "how do i remove search engines from firefox?"
date: 2005-06-06
forum: General Help
---

### Post by simianMiscreant on 2005-06-06
i have unwanted search engines cluttering the quick search box in the upper right...how do i remove them? thanks in advance.

---

### Post by krusbjorn on 2005-06-06
[QUOTE=simianMiscreant]i have unwanted search engines cluttering the quick search box in the upper right...how do i remove them? thanks in advance.[/QUOTE]

Go to where you installed firefox (probably /usr/lib/mozilla-firefox/). There should be a searchplugins/ directory in there. Go there and remove the src and gif/png file for whatever search plugin you want to remove.

Good luck!

---

### Post by Gtaylor on 2005-06-06
Is there no way to do this inside of Firefox? You'd think there would be since you can graphically add one.

---

### Post by krusbjorn on 2005-06-06
[QUOTE=Gtaylor]Is there no way to do this inside of Firefox? You'd think there would be since you can graphically add one.[/QUOTE]

none that i have found in one and a half year ;)

anyways, the search field is incredibly clumsy once you discover the quick search bookmarks.

---

### Post by simianMiscreant on 2005-06-06
[QUOTE=krusbjorn]Go to where you installed firefox (probably /usr/lib/mozilla-firefox/). There should be a searchplugins/ directory in there. Go there and remove the src and gif/png file for whatever search plugin you want to remove.

Good luck![/QUOTE]

The ones I want to remove aren't there...  :neutral:

---

### Post by IdolizingStewie on 2005-09-12
I have two copies of amazon search in the search bar. I found the searchplugins folder, but it only had one in it. I deleted that one, but I still have two in the search bar. It's not a big deal, but it's kind of annoying. Does it hide them anywhere else?

---

### Post by bored2k on 2005-09-12
[QUOTE=IdolizingStewie]I have two copies of amazon search in the search bar. I found the searchplugins folder, but it only had one in it. I deleted that one, but I still have two in the search bar. It's not a big deal, but it's kind of annoying. Does it hide them anywhere else?[/QUOTE]
 to places where they reside:
/usr/lib/mozilla-firefox/searchplugins
and
$HOME/.mozilla/firefox/ profile name /search

---

### Post by IdolizingStewie on 2005-09-12
Ok, I deleted that too and I still have both copies in the search bar. I restarted firefox to see if that would help, but nothing changed. I assume the little voice in my head telling me to try restarting the computer too is just too many years on Windows, right?

---

### Post by bored2k on 2005-09-12
[QUOTE=IdolizingStewie]Ok, I deleted that too and I still have both copies in the search bar. I restarted firefox to see if that would help, but nothing changed. I assume the little voice in my head telling me to try restarting the computer too is just too many years on Windows, right?[/QUOTE]
 Right. Restart is bad for your juju. If you deleted every amazon search bar in /usr/lib and your user's firefox directory and they still show.. well that's kinda not likely in my book =/. You could try removing them and then doing chmod -x on the /search dir in the firefox's directory.

---

