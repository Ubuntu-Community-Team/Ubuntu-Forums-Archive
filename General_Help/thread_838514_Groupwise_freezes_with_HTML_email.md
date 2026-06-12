---
title: "Groupwise freezes with HTML email"
date: 2008-06-23
forum: General Help
---

### Post by tech4 on 2008-06-23
Hello all, 

I had this issue once before but it went away and I was never able to figure out why. So, I did new install of Hardy Heron and I installed Groupwise with out issue. (Thanks to the Forum) When I open an email that is in HTML format, Groupwise freezes and Ih have to use Xkill in term to exit it. When I set force to plain text, I can open the email and it tells me to goto VIEW select HTML but it freezes when I do that as well. 

If anyone has an answer it would be great or any help at all. I'm still a little green on  Ubuntu.

---

### Post by clparker on 2008-07-06
There are some packages you have to install, I can't remember which right now, but if you check the forums, it's some package that I assume tells groupwise how to handle these types of e-mails.

---

### Post by tech4 on 2008-07-07
Yes! Thanks for the reply. I forgot I had posted this. I found out I needed to install these "libglib1.2ldbl libgtk1.2 libgtk1.2-common" to get the HTML to show with out freezing. Thanks for the help.

---

### Post by fooey on 2009-02-03
Awesome. I know this is an older thread, but I just wanted to say this fixed it for me too. HTML e-mails kept freezing my client, but that's because i didn't have the few packages listed above installed. Thanks
:D

---

