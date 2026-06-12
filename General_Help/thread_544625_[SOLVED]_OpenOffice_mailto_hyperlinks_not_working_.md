---
title: "[SOLVED] OpenOffice mailto: hyperlinks not working with Kubuntu KMail"
date: 2007-09-06
forum: General Help
---

### Post by Zill on 2007-09-06
OpenOffice:  If I use "File, Send, Document as email" then a new KMail email correctly opens up with the document attached.

However, if I click on a hyperlinked email address (eg. mailto:nobody@example.com) in OOo then nothing seems to happen - no blank email opens up.

This applies to all new and existing Calc and Writer files in OOo 2.0.2 running on Kubuntu 6.06 LTS. If I open one of these files with the same version of OOo running on Ubuntu 6.06 LTS on a different PC, then Evolution opens an email as expected.

On the Kubuntu PC "Tools, Options, Internet, E-mail" is set to "sensible-ooomua" but I have also tried "kmail" and "usr/bin/kmail" with the same results. Kmail/Kontact works fine for all other purposes.

Web links ([www.example.com](www.example.com)) also work fine with Kubuntu/OOo. Any ideas please?

---

### Post by Zill on 2007-09-08
I tried OOo with a new user and got identical behaviour.

I then ran OOo from the terminal, clicked on the email hyperlink and got the following error:
Code:
ScimInputContextPlugin()
/usr/lib/openoffice/program/kde-open-url: line 54: sensible-ooomua: command not found
~ScimInputContextPlugin()

Examination of file /usr/lib/openoffice/program/kde-open-url revealed a line near the end:
Code:
sensible-ooomua "$1" &

I commented out this line and added the new line:
Code:
kmail "$1" &

The resulting section of code now looks like this:
Code:
# special handling for mailto: uris
if echo $1 | grep '^mailto:' > /dev/null; then
#  sensible-ooomua "$1" &
  kmail "$1" &
else
  sensible-browser "$1" &
fi

email hyperlinks now work perfectly in OOo for all users :-)

---

