---
title: "ESC to close Gaim chat window?"
date: 2006-12-08
forum: General Help
---

### Post by core on 2006-12-08
Hi

I've updated from dapper to hoary and new gaim came along. It's OK, just that I'd like to close chat windows with the ESC key (I got too much used to it with MSN Messenger), and Gaim2 seems to have no such option. Does anyone know how can I make it possible?

I'm asking this because I'm almost 100% sure that Gaim 1.5 had that option. Also, I'm preety certain that after upgrade to 2.0beta, windows were still being closed with the ESC key with no problems. It's just that this time I didn't check that option when I still had 1.5, I upgraded to Egdy right away :(

Any help? Thanks.

---

### Post by endersshadow on 2006-12-08
It's Ctrl+W now...don't ask why...I don't know...I was just as upset as you were, and I was reading through the code angry, which is never good...for anybody...

---

### Post by core on 2006-12-09
> **endersshadow said:**
> It's Ctrl+W now...don't ask why...I don't know...I was just as upset as you were, and I was reading through the code angry, which is never good...for anybody...

Thanks for the info, I would never know, I'm always to busy to ckeck the source :P Well I'll try to adjust. But I'll suggest them to fix it. That's the shortcut used in Firefox, maybe it's becoming a standard?..

Thanks. But I still could swear I used to close with ESC the last time I upgraded.. oh well.

---

### Post by core on 2006-12-09
I found the answer myself, I was to lazy to read the Gaim2 FAQs.

It's an implementation option, and it now I had to edit ~/.gaim/accels, replacing

(gtk_accel_path "<main>/Conversation/Close" "[something]")

with

(gtk_accel_path "<main>/Conversation/Close" "Escape")

Thanks anyway.

---

### Post by endersshadow on 2006-12-09
Always reverts for me when I do that...

---

### Post by ve9gra on 2007-01-06
[http://gaim.sourceforge.net/faq2.php#q24](http://gaim.sourceforge.net/faq2.php#q24)

You have to uncomment that line too...

---

