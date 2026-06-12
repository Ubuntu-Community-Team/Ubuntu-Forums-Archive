---
title: "Firefox homepage displaying Spanish"
date: 2015-04-07
forum: General Help
---

### Post by Nick_W on 2015-04-07
Hi,

I've just cleared my cookies and preferences on Firefox (37) on Ubuntu 12.04 (latest updates applied a couple of days ago). FWIW I have AdBlock plus installed following recommendations from my last post.
On restarting Firefox I discovered the default about page (with Google search) is showing in Spanish.

No other sites (e.g. plain Google) show Spanish and the Firefox language preference still seems to show English.

Any idea on this? Has happened just now. I'm sure a while back (a year) it showed Arabic but then reverted to English.

Is this something I need to worry about from a security POV?
I tried restarting the computer and still got Spanish.

EDIT: It's now changed back to English again after about 10 mins. I'm sure that's what happened last time when I got Arabic. Can anyone shed light on this and whether it's a cause for concern?

EDIT again: Sorry! I've just found out I did post about the Arabic problem last year - I signed up to AskUbuntu and asked on there, then must have forgotten about it ;-) The recommendation there was to post a bug report - I will do now. Sorry for duplicate question (to another forum admittedly) but any other input would be welcome.

Thanks,
Nick

---

### Post by dino99 on 2015-04-07
did you got an April fool around ?

---

### Post by Nick_W on 2015-04-07
No ;-) It's not an April fool!

Anyway, the problem has reappeared just now; for example, it says "Pagina de inicio de Ubuntu" and "Tienda Ubuntu" for the shop.
I've just updated Firefox to todays update, FWIW.

Also, if I type in "Madrid" in the Google search box on the home page, I get results in Spanish,
By contrast on the regular Google homepage (I get redirected to google.co.uk if I enter google.com) or on about:home and try Madrid, I get English results.

So whatever it is, it's something to do with Ubuntu and Firefox together, not Firefox on its own or my Google settings.
Nothing else on my system displays in Spanish and the Ubuntu language setting has remained at English (UK).

I've lodged a bug report but seriously.... though unlikely, is there any chance of this being a "hack" on my machine? Sorry if I sound paranoid but just want to be sure. Thanks.

---

### Post by sandyd on 2015-04-07
Lets have a try:

Exit firefox, and move the firefox profile somewhere else for now
```

cd
mv .mozilla firefox-profile-backup

```

Firefox will generate a new profile on start. See if this profile will do the same.

Side note: moving your firefox profile will cause firefox to generate a new profile, meaning none of your bookmarks/extensions will be there. Your old firefox profile is now in a folder called firefox-profile-backup.

You can switch between the profiles by simply moving the .mozilla folder around.

To return to your normal firefox profile, exit firefox, and run
```

cd 
mv .mozilla firefox-profile-test
mv firefox-profile-backup .mozilla
```

If the issues remain, try another computer. If it has the same issues, you can safely assume that this is a Google issue. Google is terrible at geolocation and will sometimes think US IPs are in France/etc

To fix that... : (side note: sometimes the command will return blank, just run it again)
```

sudo apt-get install whois curl
whois `curl -s checkip.dyndns.org | sed -e 's/.*Current IP Address: //' -e 's/<.*$//'` | grep CIDR | tail -n1 | awk -F":" '{gsub(/ /, "", $0);print $2}'
```
Get the CIDR you have on the screen, go to [https://support.google.com/websearch/contact/ip](https://support.google.com/websearch/contact/ip) and use the CIDR as your IP Address

You can also use [http://google.com/ncr](http://google.com/ncr) as homepage.

---

### Post by Vinciane on 2015-04-08
Hi, I had the same thing, saw Spanish and also some Slavic language, it came and went with Software Updates, so thx for fixing that but it was still weird, couldn't have gotten work done that way, tried to look up a local phonenumber i.e, which is actually another question.
Have a nice day

---

### Post by haplorrhine on 2015-04-08
Many threads about this.
[http://ubuntuforums.org/showthread.php?t=2168103](http://ubuntuforums.org/showthread.php?t=2168103)
[http://ubuntuforums.org/showthread.php?t=2268583&highlight=firefox+start+page+language](http://ubuntuforums.org/showthread.php?t=2268583&highlight=firefox+start+page+language)

It's a one time thing here.  I refresh and it's gone.  Arabic some several days ago; Spanish last night and this morning as I ran firefox for the first time from different users after a fresh reinstall and gateway-reset (AT&T u-verse).  I swear someone has been manipulating my webpages, but I don't know that they've actually compromised the browser.

---

### Post by Nick_W on 2015-04-10
Hi, thanks for the replies. The problem has not occurred again since my last post - but if it does I will follow the advice given here.
Whatever it is... it seems to be a common problem but glad it doesn't seem to be ringing serious alarm bells with anyone.

---

### Post by eezacque on 2015-04-11
Annoying as it is, I usually fix this by resetting Firefox language to English in preferences. That is, it is already set to English, but setting it to something else and setting it back to English fixes the problem for me. I suspect it is a problem with Firefox screwing up preferences.

---

### Post by haplorrhine on 2015-04-22
Oh yeah, this baby's compromised.  I just made some usb backups to examine with my Kali laptop, and the laptop went haywire immediately after I formatted the usb.  Frantic mouse movements, windows closing themselves.  To be fair, it probably has been compromised on and off for the past several months, and I didn't see this firefox glitch until this month.

That laptop first exhibited chronic pointer tantrums 6 months ago, but it's been [s]glitch-[/s] exploit-free since I  reinstalled and made it a standalone machine, until today.

---

