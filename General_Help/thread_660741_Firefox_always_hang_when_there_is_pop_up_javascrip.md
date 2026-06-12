---
title: "Firefox always hang when there is pop up javascript"
date: 2008-01-07
forum: General Help
---

### Post by keenlearner on 2008-01-07
My Firefox version is 2.0.0.11

When there is a link that use Javascript for pop up window, My Firefox will get hang. Any idea why ? Thanks.

---

### Post by Sef on 2008-01-07
Are you using No Script?

---

### Post by keenlearner on 2008-01-08
You mean I disabled the javascript ? I am certain that my javascript is turned on.

---

### Post by tienhn on 2008-02-15
I have seen this problem as well. Javascript is ON. It is not always hangs in my case but about 30% of the time, when I have an pop up window (which I allowed), it will hang and I have to "forced quit" firefox.

---

### Post by keenlearner on 2008-02-18
It's so sad, my one hang everytime (100%) when there is Javascript pop up window. I had tried to reinstall back Firefox but it's still the same, I used the sypnatic to remove it, but I think it's not completely removed. Is there a way to to a clear remove ? Thank you.

---

### Post by z|x on 2008-02-23
I am facing the same problem here.

---

### Post by multia on 2008-03-05
I have the same problem. 
It's not 100% ALL THE TIME. The same site can crash firefox once and then I kill it and reopen the site and then it opens the popup (without asking with the yellow firefox popup prevention bar)

:confused:

---

### Post by knowname on 2008-03-20
I also have the same problem, but it seems to be fairly repeatable. If I have more than one window open, and click a javascript pop-up link, firefox will hang and cpu usage will go to max.

I'm using firefox 2.0.0.12

---

### Post by z|x on 2008-03-20
I guess we'll just have to wait for the new version of the Google Toolbar to be released. The people in the help groups also dont seem to be trying to find out a solution.

---

### Post by DarwinsTheory on 2008-03-21
Just reporting I have the same issues...

Matt

---

### Post by djcrash1981 on 2008-03-25
Mmmmmmmmmm i think there might be a bug. Because I'm having the same exact problem.
With firefox 2.0.0.12

---

### Post by djcrash1981 on 2008-03-31
> **djcrash1981 said:**
> Mmmmmmmmmm i think there might be a bug. Because I'm having the same exact problem.
With firefox 2.0.0.12

After a really calm and patient revision of the problem (In my case), what i found was this:

The problem was the google toolbar.

How did i discover it??????

Easy, first of all, i had to simulate a fresh, clean, install of firefox, so I moved all the directory ~/.mozilla to ~./mozilla.old

Then I opened the page with the conflict and It worked fine, without trouble, so the next thing I tried was installing all the extensions one by one and proving the same page.

That way I was able to find out, that the problem was the toolbar and not the firefox itself so i recommend to all is try it out. What could you expect: You will **partially loose** all your saved info on firefox (It'll be "saved" on the .mozilla.old directory).

I hope this help someone to prevent this or solve it.

Have a nice week 

And keep rocking with UBUNTU :guitar:

---

