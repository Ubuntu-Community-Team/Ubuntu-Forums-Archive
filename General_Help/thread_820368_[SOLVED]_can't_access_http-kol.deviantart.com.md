---
title: "[SOLVED] can't access http://-kol.deviantart.com/"
date: 2008-06-06
forum: General Help
---

### Post by taisao on 2008-06-06
Hello, 

Somehow I can't access the page [http://-kol.deviantart.com/](http://-kol.deviantart.com/) ? I'm guessing it is because of the character '-' ? On the same computer using windows xp I can access the page fine.

Please help :confused:

---

### Post by rraj.be on 2008-06-06
check whether the adress is 

```
[http://-kol.deviantart.com/ ?]("http://-kol.deviantart.com/ ?") 
```

or

```
[http://kol.deviantart.com/ ?]("http://kol.deviantart.com/ ?") 
```

I can acces the latter correctly.

Check whether it is the site that you are trying.

---

### Post by Joeb454 on 2008-06-06
I can also access [http://kol.deviantart.com/](http://kol.deviantart.com/) just fine :)

---

### Post by taisao on 2008-06-06
no, it's [http://-kol.deviantart.com](http://-kol.deviantart.com) , but u guys can't access that one also? The problem is most likely from ubuntu, because I can access it just fine with windowxp.

---

### Post by taisao on 2008-06-07
no one is able to load: [http://-kol.deviantart.com/](http://-kol.deviantart.com/) ?

---

### Post by ibuclaw on 2008-06-07
Hmm...

If deviantart had followed Internet URL standards, none of this would have happened in the first place...

The reason why it would load is because it is illegal to have a domain address starting with a special character (in this case, it's a hifen " **-** " ).

So as far as most servers are concerned, -kol.deviant.com is an invalid name.

Why it works for Windows? Well, they don't exactly follow standards, now then, do they?

I went to the luxury of trying to put it in a "loadable" URL for you via a URL redirection domain (freedomain.co.nr, shorturl.com, tinyurl.com, etc.), but they failed to pickup the illegal "-kol" too.

If you know any more redirection domains, then give them a try.
Other than that, there is [the google cached version.]("http://64.233.183.104/search?q=cache:d3Hfzy6HVGwJ:-kol.deviantart.com/+-kol.deviantart.com&hl=en&ct=clnk&cd=1&gl=uk")

Regards
Iain

---

### Post by taisao on 2008-06-08
thanks for the explanation :(

---

### Post by dyntryx on 2008-09-30
Kol posted this on his DeviantArt page on July 12, 2008...

[INDENT]I've been having some big problems with Linux users that are trying to visit my deviantART profile. When I first joined deviantART my username was !studio28 but I got banned because I was linking to the downloads directly from my site, very stupid. Then I joined as -kol because kol was already taken. I don't know who ~kol is but he have never been active here on deviatnART. Anyways I had to add a dash in front of my username and after a while I started to received emails about Linux user not been able to access my deviantART profile. I found that the problem is the dash in front of my username. :( This is what the Help section in dA says about the problem: [[link]("http://help.deviantart.com/664/")]


My friends username has a dash before, after it or both and I cannot access their page. Why is this?

This is normal as they're not standard host naming (aka considered illegal char naming). In IE such usually works, however not in Firefox or on Linux.

To stop this we no longer allow such naming of accounts.

If you have an account with such, you may wish to create a new username.



Workaround:

This workaround has been successfully tested on SuSE Linux 10.3

You will need to add a line to your /etc/hosts file, with deviantART's dotted-quad address and .deviantart.com as the symbolic name, for instance:

198.172.81.21 -electra-. deviantart.com

(If you have several dA friends with usernames beginning or ending in a dash, you'll need such a line for each of them, with the same numeric address 198.172.81.21). Of course, any such line will have to be changed if the dA site changes its IP address someday.

Possible ways to determine dA's IP address is by looking at the heading line of the output of
- Windows: tracert www. deviantart.com
- Linux: traceroute www. deviantart.com


Note: Editing /etc/hosts usually requires superuser privileges. If you don't have them, you will probably need help from a sysadmin (of your system, not a dA admin).

Workaround provided by *tonymec


Looks like there is a workaround but my other option is to create another account, something that I'm not going to do because I'm going to loose all my stats and everything.
Also the other days I was browsing dA from my iPhone with firmware 1.1.4 and I find out that I couldn't access my profile from the iPhone either but with firmware 2.0 looks like they fixed something because now I can. :)

Right now deviantART is the only place I upload my work and it sucks that Linux users can't access my account but it looks that I'll have to deal with it.[/INDENT]

If I go to the terminal and type:
```
ping deviantart.com
```
I get...
```
PING deviantart.com (8.10.77.140) 56(84) bytes of data.
```

So since the IP is currently 8.10.77.140, you can edit your hosts file by typing:
```
gksudo gedit /etc/hosts
```

Add this to that file..
```
# Workaround for dashes in URLs
8.10.77.140 -kol.deviantart.com
```

Hope that helps.

---

### Post by twisted_steel on 2009-01-19
> **dyntryx said:**
> Add this to that file..
```
# Workaround for dashes in URLs
8.10.77.140 -kol.deviantart.com
```Hope that helps.

Perfect! Now I can finally download the wallpapers :)

---

