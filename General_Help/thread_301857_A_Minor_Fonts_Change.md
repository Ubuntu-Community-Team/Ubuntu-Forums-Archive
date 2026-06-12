---
title: "A Minor Fonts Change"
date: 2006-11-17
forum: General Help
---

### Post by Greg T. on 2006-11-17
Font preferences are often a matter of personal taste, but I offer up the following in case anyone is interested. Compare the two screenshots attached to this post. One screenshot was taken from a default install of Dapper; note the faded stems on the lower-case letters "k" in particular. The other is  the same text after I applied the change described below; in my opinion, it's an improvement. 

To do this, I'll presume you already have set up the Microsoft core fonts (msttcorefonts). If this isn't the case, you can easily find out how to do so by a simple search on this site.

You'll need to edit etc/fonts/local.conf (or ~/.fonts.conf) to include the following:

```
<!-- Eliminate washed out "k" and "x" in Verdana & Tahoma -->

<match target="font">
  <test name="family">
    <string>Verdana</string>
  </test>
  <edit name="autohint">
    <bool>true</bool>
  </edit>
</match>

<match target="font">
  <test name="family">
    <string>Tahoma</string>
  </test>
  <edit name="autohint">
    <bool>true</bool>
  </edit>
</match>

```
I suggest adding this before the closing "</fontconfig>" tag in the file.

Restart X (ctrl-alt-bksp) or reboot. That should do the trick.

---

