---
title: "web development: firefox problem when updating the dom"
date: 2007-02-27
forum: General Help
---

### Post by egonh on 2007-02-27
Hi All,

I'm sorry but this little problem is driving me nuts. I've attached a test file: [ATTACH]26284[/ATTACH]  which just update an unordered list with a list item when you click "crash". What happen in version 2.0.0.2 is the following:

[LIST=1]
[*]If the javascript console is closed, firefox just opens it (with no error message whatsoever). This is very annoying to the end user because the firefox window lose focus.
[*] If the javascript console is already open, it just won't let the user change any of the form fields available, as if they were read-only.  If it wasn't strange enough, when the user change focus to another application window, and then back to firefox, the form fields go back to their previous state.
[/LIST]



Weird isn't it? I'm building a web 2.0 application and this can be very annoying when updating any dom element. I couldn't find anything in google and have found the same problem in another edgy box. Have anyone had the same problem? Should I file a bug in firefox?

Any help would be greatly appreciated.

Thanks in advance.

Egon

---

### Post by davekenny on 2007-02-27
change the 'javascript:' to
'javascript: crash('mylist')'
also remove the onclick event.  leaving the onclick event calls the function twice.
it seems firefox is trying to call other javascripts since one ins't listed.

sorry I don't know why this works but it does. and doesn't crash firefox

-dkenny

---

### Post by egonh on 2007-02-28
Thanks man! it worked!

It worked on firefox 1.5.x, thats why I thought it was so strange... but that will solve my problems.

Thanks again :)

---

