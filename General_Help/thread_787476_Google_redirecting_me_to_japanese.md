---
title: "Google redirecting me to japanese"
date: 2008-05-08
forum: General Help
---

### Post by dondad on 2008-05-08
If I type [www.google.com](www.google.com) into the address bar, it redirects me to [http://www.google.co.jp/ig?hl=ja](http://www.google.co.jp/ig?hl=ja) no matter what I do. This is in Hardy with FF2. Firefox 3 does basically the same thing except that it goes to igoogle in japanese. Any ideas as to what I can do to fix it? I have another box with gutsy and FF2 and it started doing the same thing at around the same time. I also have Windows in a virtualbox and it is messed up in Firefox and IE also. As far as I know, I haven't done anything with DNS or changed any router settings. If I put in the actual IP address of Google, it works fine.

Just as a check, I did 
```

host www.google.com 

```
in the terminal, and got the correct IP addresses. 

This is weird and I have no clue where to look now. I have heard of issues with opendns, but I have never used nor even heard of it until now.

---

### Post by Bubba64 on 2008-05-08
Right next to the search bar is preference in IGoogle choose your language and then hit save preference.

---

### Post by dondad on 2008-05-08
> **Bubba64 said:**
> Right next to the search bar is preference in IGoogle choose your language and then hit save preference.

One of the first things that I tried was to set the preferences, but nothing. Also, how does Google know who I am except for a cookie and this has happened in two gutsy installs, one hardy, and in IE and firefox in Windows running in a virtual box.

---

### Post by dondad on 2008-05-10
Another thing that I tried: I put the ip address that works in my hosts file mapped to [www.google.com](www.google.com) and still get the same japanese page. I checked the dns servers in my router and they seem to be the ones from Comcast and I haven't changed anything. Any clues why the hosts doesn't work.

This is my hosts file:
```

127.0.0.1 localhost
127.0.1.1 family-desktop
64.233.167.104 www.google.com



# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts


```



I also tried mapping [www.google.com](www.google.com) to 127.0.0.1 to see if it would not open. Nothing changed. I did the same thing to [www.microsoft.com](www.microsoft.com), and it was blocked. This only seems to affect Google. I am at a loss even where to look.

---

### Post by rubicon on 2008-05-10
The prob is **not** on your side. Google looks on **your** ip and thinks you're from Japan. That's basically all.

You just said that you've been **redirected**, so who did redirect you? ;)

---

### Post by jespdj on 2008-05-10
Check this:

In Firefox go to Edit / Preferences / Content. Below Languages, click the "Choose..." button. Check if the languages in the list are what you want, change them if necessary.

---

### Post by Thanoulis on 2008-05-10
Check your OS locate setting.

---

### Post by dondad on 2008-05-11
> **rubicon said:**
> The prob is **not** on your side. Google looks on **your** ip and thinks you're from Japan. That's basically all.

You just said that you've been **redirected**, so who did redirect you? ;)

I don't know if redirect is the right term. I type [www.google.com](www.google.com) into the address bar and it automagically changes to [http://www.google.co.jp/](http://www.google.co.jp/). I can get to the english google by typing the google ip address. I tried adding [www.google.com](www.google.com) to the hosts file with the google ip address and it made no difference. Same change to the address bar. I then changed it in the hosts file to [www.yahoo.com](www.yahoo.com) with the google ip address and when I type [www.yahoo.com](www.yahoo.com), I get google in english. No clue where to go from here.

---

### Post by dondad on 2008-05-11
> **jespdj said:**
> Check this:

In Firefox go to Edit / Preferences / Content. Below Languages, click the "Choose..." button. Check if the languages in the list are what you want, change them if necessary.

In my content for Firefox under content, there is no language entry.

---

### Post by dondad on 2008-05-11
> **Thanoulis said:**
> Check your OS locate setting.

How do I do that?

---

