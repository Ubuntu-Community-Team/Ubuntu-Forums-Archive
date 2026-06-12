---
title: "Issue with java in chrome."
date: 2013-02-09
forum: General Help
---

### Post by gigabz666 on 2013-02-09
This is a weird and very specific issue, but just a little annoying. When I use find a member on [www.bowl.com](www.bowl.com) in Chrome, I'm getting a java error as follows.
```

Error: javax.servlet.jsp.JspException: In <parseDate>, value attribute can not be parsed: "7/31/2013" 
```

This happens in both Google Chrome and Chromium. However, if I use Firefox, the website works as expected and there is no java issue.

So basically I'm wondering if I'm alone in this, or do other people find this issue. I feel like this is at least a Chrome/Ubuntu issue and maybe Chrome/Linux, because it works in Chrome on a Mac, and I believe someone else used Windows and it was fine. So for some reason this website doesn't like the combination of Chrome and Ubuntu.

I use the following (it's my profile) but it's the same with any profile.
[http://membership.bowl.com/USBCsearch/ViewMember.jsp?prefix=11&suffix=609594](http://membership.bowl.com/USBCsearch/ViewMember.jsp?prefix=11&suffix=609594)

EDIT: Well now it's not working on Firefox either. I tried installing openjava (I was originally using Oracle Java) and seeing that not working, I went back to Oracle and now I'm getting the same error in Firefox. So I guess this is an issue with java on my computer.

---

### Post by gigabz666 on 2013-02-18
I seem to have fixed this. It looks like the java error is due to a language issue. I had my browser set to English (United Kingdom) by default and to use it for the spellchecker. Once I switched the priority to English (United States) but kept spellchecker to UK, the error no longer appeared. Weird, but maybe this will help anyone else who runs into this issue in the future.

---

