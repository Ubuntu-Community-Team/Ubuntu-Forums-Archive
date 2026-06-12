---
title: "Gnucash, Segfault when Exporting Invoices"
date: 2007-10-24
forum: General Help
---

### Post by mofodojodino on 2007-10-24
Hi Guys,

I've just completed a clean install of 7.10 on my laptop and I installed GnuCash so that I can track my business and create invoices. Only problem is that I want to use a script which allows me to use LaTeX to create far more customised invoices than Gnucash is able to do ([http://stefans.datenbruch.de/gnucash/gc2latex.shtml](http://stefans.datenbruch.de/gnucash/gc2latex.shtml) for more info).

The problem I have found is that this LaTeX script requires you to export your invoices from Gnucash using the menu Business -> Export -> QSF Invoice... and every time I do this Gnucash just Segfaults and give me no more information. I have tried using the other export functions in that menu and they all work fine except the QSF Invoices... which is rather annoying.

If anyone has a work around or permanent fix for this problem I would really appreciate it.

Cheers
Dino

---

### Post by mofodojodino on 2007-10-24
Here is some more info from running it in debug mode.

* 10:01:30  INFO <gnc.backend> [gnc_determine_file_type]  new file
* 10:01:30  INFO <qof.session> [qof_session_load_backend]  selected GnuCash File Backend Version 2
* 10:01:30  INFO <qof.session> [qof_session_begin] Done running session_begin on backend
* 10:01:30  INFO <gnc.account> [xaccAccountRecomputeBalance] acct=Accounts Receivable starting baln=0/1
* 10:01:30  INFO <gnc.engine> [xaccTransSetDateInternal] addr=0x8286d00 set date to 1193270266.000000000 Thu Oct 25 09:57:46 2007
* 10:01:30  INFO <gnc.engine> [xaccTransSetDateInternal] addr=0x8286d00 set date to 1193234400.000000000 Thu Oct 25 00:00:00 2007
* 10:01:30  WARN <GLib-GObject> instance of invalid non-instantiatable type `(null)'
Segmentation fault (core dumped)

Cheers
Dino

---

