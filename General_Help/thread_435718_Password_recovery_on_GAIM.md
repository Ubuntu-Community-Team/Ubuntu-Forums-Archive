---
title: "Password recovery on GAIM"
date: 2007-05-07
forum: General Help
---

### Post by suhaib on 2007-05-07
Ok this is a bit of a strange one...

Sadly and stupidly, I have forgotten the password to one of my MSN accounts.  Thankfully, I told GAIM to remember the password, so I can still login to use the messenger!  However, I cannot login to my inbox or use the account on another machine.

For some reason when I answer my secret question (on hotmail.com) it doesn't work, I mean I know my damn pets name (unless I put a silly answer lol)!

When I modify the account on GAIM, the password appears masked.  Is there anyway of unmasking it or copying it, since when I copy and paste it into a document, it remains masked.

Thanks.

---

### Post by hyperair on 2007-05-07
Disclaimer: Please do not use these instructions to get your friends' passwords or something equivalent. It's not pleasant and you should respect their privacy. I will not be responsible for anybody's account being hacked as a result of this. 

Here's what you do:

1. Enter your Home directory from Nautilus
2. Show hidden files (Ctrl+H)
3. Navigate into your ".gaim" folder
4. Open accounts.xml in Firefox. You'll see it in a tree form.
5. Beside each <account> tag there is a "-" sign. Click each one except the first one to collapse most of the tree. You should end up with something like this:
```

- <account version="1.0">
   + <account></account>
   + <account></account>
   + <account></account>
   + <account></account>
   </account>

```
6. In each of the <account> tags (expanded one by one), you should find a <name> tag, and a <password> tag. Your password is located <password>here</password>


For those in multiuser environments, don't worry, it is only read and write accessible to the owner of the file which is you. If you don't let anybody use your account they can't read it (unless they have sudo powers)

---

