---
title: "mail-notification open www.gmail.com"
date: 2005-05-16
forum: General Help
---

### Post by jasplund on 2005-05-16
I've installed mail-notification

It would be great if I could double click the letter in the notification area to open [www.gmail.com](www.gmail.com) with firefox? Is there a way to do this. It can launch a mailreader that way. What command should I use to make [www.gmail.com](www.gmail.com) my mailreader?


Thanks Johan

---

### Post by lao_V on 2005-05-16
I haven't used the app personally, but, there should be an option to set up your mailboxes as illustrated in the [screenshot]("http://www.nongnu.org/mailnotify/screenshot.png")?

---

### Post by lorap on 2005-05-16
hi friend!
i've been trying myself to work with mail notificating, but it fails to run with gmail.
it's not a bug but probably authorization case.
if you check you'll see that it does work with some others mail providers, but with some not.

---

### Post by jasplund on 2005-05-16
[QUOTE=lao_V]I haven't used the app personally, but, there should be an option to set up your mailboxes as illustrated in the [screenshot]("http://www.nongnu.org/mailnotify/screenshot.png")?[/QUOTE]

I know how to get it to check my gmail account. The thing is that I want it to open firefox when I click on the icon. I can write the command mozilla-firefox to get it to open firefox when I click the icon but what should I write so it opens a specific URL? ([www.gmail.com](www.gmail.com))

---

### Post by lao_V on 2005-05-16
You can open the url [www.gmail.com](www.gmail.com) by appending it to the mozilla-firefox command but I don't think you will be able to go directly to your inbox on your browser as normally the link is generated dynamically.

The only place I have seen this done is in msn/gaim with hotmail account

---

### Post by jasplund on 2005-05-16
[QUOTE=lao_V]You can open the url [www.gmail.com](www.gmail.com) by appending it to the mozilla-firefox command but I don't think you will be able to go directly to your inbox on your browser as normally the link is generated dynamically.

The only place I have seen this done is in msn/gaim with hotmail account[/QUOTE]


But how do I do that?


Johan

---

### Post by lao_V on 2005-05-16
mozilla-firefox %[www.gmail.com](www.gmail.com) (you may or may not need %)

---

### Post by brickbat on 2005-05-16
Do you mind if I ask how you got mail-notification working with gmail.  I tried the on in the repository and I downloaded a .deb package of 1.1 and they both crash on me.

ciao
bb

---

### Post by jasplund on 2005-05-16
[QUOTE=brickbat]Do you mind if I ask how you got mail-notification working with gmail.  I tried the on in the repository and I downloaded a .deb package of 1.1 and they both crash on me.

ciao
bb[/QUOTE]

I use the one from the repositories. I use my e-mail address as username (incl @gmail.com). It doesn't work though if I don't have any delay between checks.

---

### Post by jasplund on 2005-05-16
[QUOTE=lao_V]mozilla-firefox %[www.gmail.com](www.gmail.com) (you may or may not need %)[/QUOTE]

mozilla-firefox [www.gmail.com](www.gmail.com) works but not with the %. The only problem is that it opens in the latest tab. I'd like it to open in a new tab.


Johan

---

### Post by jasplund on 2005-05-17
[QUOTE=jasplund]I use the one from the repositories. I use my e-mail address as username (incl @gmail.com). It doesn't work though if I don't have any delay between checks.[/QUOTE]

btw the language in gmail must English

---

### Post by lao_V on 2005-05-17
You can configure the tab behaviour in Firefox Preferences under Tabbed Browsing

---

### Post by jasplund on 2005-05-17
[QUOTE=lao_V]You can configure the tab behaviour in Firefox Preferences under Tabbed Browsing[/QUOTE]


Nope it doesn't work. I guess it only works if I open firefox with the command "mozilla-firefox" but in this case I use "mozilla-firefox www.gmail.com"

---

