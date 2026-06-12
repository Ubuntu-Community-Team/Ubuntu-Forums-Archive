---
title: "ATK (?) error message from firefox form entry problem"
date: 2022-11-05
forum: General Help
---

### Post by ceblair on 2022-11-05
I have been having problems using firefox 106.0.5 for several weeks.

   When I try to sign in to an online account, giving username
and password, nothing happens when I type things on the keyboard.
I have sometimes been able to deal with the problem by clearing
the browser history and cache, but the same thing keeps happening
later when I try to fill in forms.  When I scroll down a page,
I am often taken back to the top.

   I have noticed that, when the browser is first launched, I
am getting the message:

> Gtk-Message: 07:57:41.687: Not loading module "atk-bridge":
> The functionality is provided by GTK natively. Please try to
> not load it.

   I suspect this is related  to a message that seems to
be created later in the browser session:

> ** (firefox:185593): CRITICAL **: 08:05:31.011:
>   impl_get_StartIndex: assertion 'ATK_IS_HYPERLINK (link)'
>   failed

   Another message that I have noticed less often:
   
> glean_core::metrics::ping Invalid reason code startup for
>  ping newtab

   Thanks very much for any help!

---

### Post by tea for one on 2022-11-05
Have you tried Firefox Safe Mode?
If Firefox is open > Help > Troubleshoot Mode

---

### Post by ceblair on 2022-11-07
I did not know what I was doing, but after a session with "Troubleshoot," the problem seems to have gone away.  I am still seeing the message about not loading ATK, but I am no longer seeing the "Critical error - ATK is not hyperlink" message, and the browser seems to be working.

Thank you!

---

