---
title: "Gtk-CRITICAL ... assertion 'GTK_IS_WIDGET (widget)' failed"
date: 2022-07-05
forum: General Help
---

### Post by markfilipak-linux on 2022-07-05
Sorry, I don't usually precede a report with excuses but...

I tried to report a bug to gtk.org. I had to install an 'apport' package
```

mark@mark-VirtualBox:~$ ubuntu-bug -w

Command 'ubuntu-bug' not found, but can be installed with:

sudo apt install apport

mark@mark-VirtualBox:~$ sudo apt install apport
[sudo] password for mark:         
-----snip-----

```
I ran 'ubuntu-bug -w'. It failed.
```

mark@mark-VirtualBox:~$ ubuntu-bug -w

*** 

After closing this message please click on an application window to report a problem about it.

Press any key to continue... 


*** Collecting problem information

The collected information can be sent to the developers to improve the
application. This might take a few minutes.
..........

*** Problem in python3.8-minimal

The problem cannot be reported:

This is not an official Linux package. Please remove any third party package and try again.

```

I have no choise but to report it here. Again, sorry.

```

Persuant to https://docs.gtk.org/glib/func.critical.html
"Logging of a critical error is by definition an indication of a bug somewhere in the current program (or its libraries)."

Update Manager (mintUpdate) log (/tmp/mintUpdate/952kecim):

07.05@13:31 ++ Install requested by user
07.05@13:31 ++ Will install gnupg-utils
07.05@13:31 ++ Will install gpg-wks-client
07.05@13:31 ++ Will install gnupg-l10n
07.05@13:31 ++ Will install gpg-wks-server
07.05@13:31 ++ Will install gpg
07.05@13:31 ++ Will install dirmngr
07.05@13:31 ++ Will install gpgv
07.05@13:31 ++ Will install gnupg
07.05@13:31 ++ Will install gpg-agent
07.05@13:31 ++ Will install gpgconf
07.05@13:31 ++ Will install gpgsm
07.05@13:31 ++ Will install openssl
07.05@13:31 ++ Will install libssl1.1
07.05@13:31 ++ Ready to launch synaptic

(synaptic:7604): Gtk-CRITICAL **: 13:31:25.431: gtk_widget_hide: assertion 'GTK_IS_WIDGET (widget)' failed
07.05@13:31 ++ Return code:0
07.05@13:31 ++ Install finished
07.05@13:31 ++ Starting refresh (local only)
07.05@13:31 ++ System is up to date
07.05@13:31 ++ Refresh finished

```

---

### Post by grahammechanical on 2022-07-05
This is an user forum. We are not Ubuntu developers. This bug report to  us will go no where. This is how we report bugs in Ubuntu.

[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

Regards

---

### Post by markfilipak-linux on 2022-07-05
> **grahammechanical said:**
> ... [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs) ...

'https://help.ubuntu.com/community/ReportingBugs', clicking the <create a Launchpad account> link, takes me to
'https://help.launchpad.net/YourAccount/NewAccount', clicking the <account sign-up> link, takes me to
'https://launchpad.net/+login', says "You are already logged in", so (looking on the ribbon bar), clicking the <Launchpad> link, takes me to
'https://launchpad.net/' where there is no link/button/page to actually submit the bug report.

How do I submit this bug to GTK?

Note: I see that gtk.org is working now. However, it runs me around similarly to the above.

---

