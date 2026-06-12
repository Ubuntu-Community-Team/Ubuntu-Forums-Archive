---
title: "Removing the Firefox 2.0 search button"
date: 2006-10-30
forum: General Help
---

### Post by srunni on 2006-10-30
Hi,

I just updated to Firefox 2.0. I was wondering if anybody knew the about:config tweak that would let me remove the button on the integrated search bar. 

Thanks!

---

### Post by Zdravko on 2006-10-30
Why would I do this? It saves you from a lot of boring and repetetive typing, like google.com, wikipedia.org, etc.

---

### Post by marcog on 2006-10-30
I think he was referring to the button on the right of the search bar, like removing the "Go" button to the right of the location bar. AFAIK there is no way to remove it in about:config.

---

### Post by Zdravko on 2006-10-30
Even so I don't understand why on Earth will someone remove this item? It was designed and placed exactly there - for it has its own purpose.

---

### Post by bollix47 on 2006-10-30
Have a look [here]("http://forums.mozillazine.org/viewtopic.php?t=463668") for removing button.

userChrome.css [examples]("http://www.extensionsmirror.nl/index.php?showtopic=96").

---

### Post by srunni on 2006-10-30
I want to remove the button because I am a keyboard shortcut freak. I rarely go and click on the search box; I use ctrl+k I rarely click on the icon to change the search engine; I use alt+down. I don't click on the address bar to type in a URL; I use ctrl+l. There is no use for a button for me to click on to initiate the search, not to mention the fact that it's really annoying having it there when I've been using Firefox since 1.0 and it's never been there. The fact that the button looks really bad in Noia pretty much seals it.

---

### Post by srunni on 2006-10-31
I finally figured it out:
At [http://ffextensionguru.wordpress.com/](http://ffextensionguru.wordpress.com/) I found the following:

> To remove the search button (magnifying glass) add this line:

    .search-go-button-stack { display: none !important; }

To remove the ‘Go’ Button on the navigation bar add this line:

    #go-button-stack { display: none !important; }

If you also want to remove the search engine drop-down button as this line:

    .searchbar-engine-button { display: none !important }
All this stuff goes in your userChrome.css file, which is located in ~/.mozilla/firefox/********.default/chrome. If you don't have a userChrome.css file there, just make one.

---

