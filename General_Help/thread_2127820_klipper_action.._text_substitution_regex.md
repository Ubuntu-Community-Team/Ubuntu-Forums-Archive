---
title: "klipper action.. text substitution regex"
date: 2013-03-21
forum: General Help
---

### Post by betlog on 2013-03-21
I'm trying to make an action that replaces part of the clipboard text.
I'm not sure if my regex is wrong, or if I am just making the action wrong.

eg: I copy this text to clipboard:
[ftp://user@ftp.site.com/public_html/2013/0001-y600px.jpg](ftp://user@ftp.site.com/public_html/2013/0001-y600px.jpg)
and the action uses this regex to alter the text
s/^ftp:\/\/user\@ftp\.site\.com\/public_html\//http://site\.com\/
to convert 
[ftp://user@ftp.site.com/public_html/2013/0001-y600px.jpg](ftp://user@ftp.site.com/public_html/2013/0001-y600px.jpg)
into 
[http://site.com/2013/0001-y600px.jpg](http://site.com/2013/0001-y600px.jpg)

But then I get lost with adding the "command" and "output handling" sections to the klipper action.
I have selected the "add to clipboard" option for "output handling" so I assume  should see the new text on the clipboard.....?

Can anyone help me out?

---

### Post by betlog on 2013-03-21
[URL="ftp://user@ftp.site.com/public_html/2013/0001-y600px.jpg"]```
 ftp://user@ftp.site.com/public_html
```[/URL] works fine as the regular expression to allow klipper to recognise it as a valid action string and show it in the menu...
```
echo firefox %s | sed 's/^ftp:\/\/user\@ftp\.site\.com\/public_html\//http://site\.com/' >>/tmp/output.txt
```works as expected..
However:
```
echo %s | sed 's/^ftp:\/\/user\@ftp\.site\.com\/public_html\//http://site\.com/' | firefox
```opens firefox but doesn't seem to pass the URL parameter because it just goes to default (a blank page)

I don't get it.

---

### Post by betlog on 2013-04-02
As usual, as soon as I forget about it and come back a few days later, why it's failing immediately comes to me:

firefox "$(echo %s | sed 's/ftp:\/\/username@ftp\.domainname\.domansuffix\/public_html/http:\/\/domainname\.domainsuffix/')"

---

