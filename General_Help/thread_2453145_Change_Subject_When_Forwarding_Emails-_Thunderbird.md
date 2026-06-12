---
title: "Change Subject When Forwarding Emails- Thunderbird"
date: 2020-11-03
forum: General Help
---

### Post by mrkeef on 2020-11-03
I use a filter in Thunderbird to automatically forward some emails to my Evernote account.
I would like to be able to add the following to the Subject header @Updates. This ensures that the email is put into the Updates notebook.
Does anyone know of any way of doing this either in Thunderbird (maybe an extension) or some other mail application?
Thanks
Keith

---

### Post by dragonfly41 on 2020-11-04
My first thought on reading this is to Google search for "parsing Thunderbird reply" and this does
bring up [some ideas to follow up]("https://remusao.github.io/posts/parsing-thunderbird-msg-filters.html").

---

### Post by SeijiSensei on 2020-11-04
If you control the mail server, this is trivial using procmail to handle the delivery and its partner formail to rewrite the header.

---

### Post by HermanAB on 2020-11-05
Procmail is the standard way to modify mail messages on the fly.

---

### Post by mrkeef on 2020-11-09
Thank you for those suggestions. I appreciate your help.
I will try out the procmail option.

---

### Post by SeijiSensei on 2020-11-10
> **SeijiSensei said:**
> **If you control the mail server**, this is trivial using procmail to handle the delivery and its partner formail to rewrite the header.

Just a reminder this only works if you control the mail server.

---

