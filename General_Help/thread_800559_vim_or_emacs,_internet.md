---
title: "vim or emacs, internet?"
date: 2008-05-19
forum: General Help
---

### Post by perillux on 2008-05-19
is it possible to view web pages with the vim(vi) or emacs editor?

I don't expect to see animations or even any recognizable format.  I'd be happy just being able to view the page sorce, or maybe some limited page formating.

Then, providing the answer to the above is yes... would it be possible to actually log into webpages, such as this one, and actually make posts?  I know I'm probably stretching it, but I gotta know  :)

---

### Post by sdennie on 2008-05-19
Possibly.  But, if you are looking for a text based browser, you could try out lynx.

---

### Post by bingoUV on 2008-05-20
Sure, why not. See the attached images.

---

### Post by perillux on 2008-05-20
it's not working for me.  I typed:
vim 'http://ubuntuforums.org/showthread.php?p=4999228#post4999228'

and I got a blank vim screen with:
"http://ubuntuforums.org/showthread.php?p=4999228#post4999228" [New DIRECTORY]

at the very bottom of the terminal.

---

### Post by bingoUV on 2008-05-20
Oh, I forgot Ubuntu installs only vim-minimal by default. Try installing vim-enhanced , or other vim add-ons. Searching for vim in Add/Remove Programs should give you the options.

Also, I am not sure vim will be able to login. See the options in curl to do that. One option that logs in successfully (-b) is to send the cookie (get the cookie value from firefox after logging in persistently).
```

man curl

```

---

