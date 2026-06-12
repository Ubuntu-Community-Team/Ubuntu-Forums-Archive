---
title: "Login / Lock Screen Displaying in Strange Way"
date: 2016-05-14
forum: General Help
---

### Post by Gottier on 2016-05-14
I came to work this morning and started my computer, and everything seemed normal, except after signing in I had no network services. If I went to System Settings -> Network it told me "**The system network services are not compatible with this version**". That's really great error message you know. I had not done anything to deserve this!

So I looked around online, and finally found a solution that worked:

```
sudo dhclient
sudo apt-get update
sudo apt-get upgrade
```

Ubuntu did it's thing, and then I restarted the computer. Now the login / lock screen looks a little different:

1) The place where I type a password is a white box, instead of the styled box that is usually there.
2) The computer name ( or host name ) that is in the upper left corner has a white background and black letters.
3) The icons in the top bar look smushed.
4) The time in the top bar is barely visible, because it is now black characters on a grey background.

I'd take a screenshot if I could, but the screenshot feature doesn't work on the login / lock screen.

I haven't had the chance to see if anything else is broken, but once logged in the computer seems fine. What's wrong with the login / lock screen?

---

### Post by Gottier on 2016-05-14
I figured it out. Somehow the accessibility option for High Contrast got checked. I unchecked it and all is well. I'm still not delighted that I had the network connectivity issue, but it would seem that things are back to normal.

---

