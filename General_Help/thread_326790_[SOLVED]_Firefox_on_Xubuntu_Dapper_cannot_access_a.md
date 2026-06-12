---
title: "[SOLVED] Firefox on Xubuntu Dapper cannot access a web page, but OK in Windows XP"
date: 2006-12-28
forum: General Help
---

### Post by Barely Here on 2006-12-28
Hello

On my Xubuntu Dapper box with Firefox 1.5.08, I cannot access the internet banking log-in page of HSBC Bank Australia. When I try it the site would ask for Internet Explorer or Netscape.

link: [http://www.hsbc.com.au/](http://www.hsbc.com.au/)
The log-in in question is through the upper left hand corner 'internet banking' javascript link

On my Windows XP box with Firefox browser, I CAN access that log-in page though.

Question:
1. Does this problem occur in your machine?
2. What can be done to fix this?

---

### Post by Olav on 2006-12-28
> **Barely Here said:**
> Hello

On my Xubuntu Dapper box with Firefox 1.5.08, I cannot access the internet banking log-in page of HSBC Bank Australia. When I try it the site would ask for Internet Explorer or Netscape.

link: [http://www.hsbc.com.au/](http://www.hsbc.com.au/)
The log-in in question is through the upper left hand corner 'internet banking' javascript link

On my Windows XP box with Firefox browser, I CAN access that log-in page though.

Question:
1. Does this problem occur in your machine?

Yes.

> 2. What can be done to fix this?

Write them a nasty e-mail (okay, perhaps a polite one) that they are a bunch of amateurs (okay, perhaps just a bit biased toward a specific OS) and that their javascript is unnecessarily blocking out users who would otherwise be perfectly able to use their banking stuff.

There is NO fundamental difference between Firefox on Windows and on Linux that would make the one more suitable than the other.

Really, this is just incompetence on their part. For as long as you still have to put up with it, you could always install Internet Explorer 6 with Wine, see: [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Internet_Explorer_.2B_Flash_9_.28IEs4Linux.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Internet_Explorer_.2B_Flash_9_.28IEs4Linux.29) 

(it has helped me on a few of such occasions, amazing that it works actually)

---

### Post by Barely Here on 2006-12-29
Olav,

Thank you for your help. Glad to know that I'm not the only one experiencing this problem.

I've sent them an email telling them to:
Stop asking for vendor specific browser, instead they should embrace Internet Standards, and
Stop being picky about OS too.

Let's see how they'll respond.

For Internet Explorer, I can alway dual-boot back to Win98....

---

### Post by maxamillion on 2006-12-29
If you really **_have to have_** internet explorer, you might check out [http://www.tatanka.com.br/ies4linux/page/Main_Page](http://www.tatanka.com.br/ies4linux/page/Main_Page)

---

### Post by haiku99 on 2006-12-29
Opera (in Ubuntu) might work, I've had success in a similar situation....

---

### Post by Olav on 2006-12-29
Here's another thing you could try: [https://addons.mozilla.org/firefox/59/](https://addons.mozilla.org/firefox/59/)

It lets you change the identification string that the browser sends to the server, fooling the server to think that you are using another browser than you are actually using. Some of those "browser detection" scripts are actually stupid enough to fall for it.

**Just tried:** your banking site seems to be stupid enough indeed. Of course I don't have the data needed to log in, but at least it does not give the error you previously described.

---

### Post by SteveHoffmanUK on 2007-01-01
I had a similar problem trying to view my son's blog - fine in WindowsXP, error message in Ubuntu 6.06 Dapper Firefox2.0. Someone suggested doing the following, which worked in my case:

Clear your Firefox browser address window and type in: "about:config" (without the quotes, of course). This will bring up a long list of settings in alphabetical order. Scroll down to the one called "network.dns.disablelPv6". if its value is "false", toggle (double-click) it so that it reads "true", then try to access the bank's website.

Don't ask me what this setting is; I never bothered to find out. I just know that the change worked for me.:cool:

---

### Post by tyinfitz on 2007-03-21
G'Day,

I just logged into my HSBC.com.au account with the fire fox user agent switcher ([https://addons.mozilla.org/firefox/59/](https://addons.mozilla.org/firefox/59/)) and checked my balance.

Once it is installed open firefox and goto

Tools -> User Agent Switcher -> Internet Explorer

Ensuring that IE is selected (the mistake i first made thinking it would auto config or something). Hope this helps, I've only been using it a few days myself.

Regards
tyinfitz

--
Normally I'd have something witty here but i haven't configured it yet ;-)

---

### Post by darell_m on 2007-06-07
I am in Egypt and HSBC only works under IE so use switcher

---

### Post by viking777 on 2007-08-13
I have the same problem with HSBC, I have just tried both the solutions offered here and neither works for me. Incidentally it is exactly the same with Konqueror, that won't load the page either, yet Firefox on Windows (with *exactly* the same settings) will load it every time. The problem with Linux (it is not just a Ubuntu problem the same occurs on PCLOS) is that it does not load the pop up window in which you enter your login details (date of birth, password, etc) it just goes straight to the page that says 'login details incorrect' (of course they are, I never got the chance to enter any!). Any yes I have tried it with 'block pop up windows' switched off and the result is just the same. I am using Firefox 2.0.0.6 on both Windows and Linux.

---

### Post by darell_m on 2007-08-14
> **viking777 said:**
> I have the same problem with HSBC, I have just tried both the solutions offered here and neither works for me. Incidentally it is exactly the same with Konqueror, that won't load the page either, yet Firefox on Windows (with *exactly* the same settings) will load it every time. The problem with Linux (it is not just a Ubuntu problem the same occurs on PCLOS) is that it does not load the pop up window in which you enter your login details (date of birth, password, etc) it just goes straight to the page that says 'login details incorrect' (of course they are, I never got the chance to enter any!). Any yes I have tried it with 'block pop up windows' switched off and the result is just the same. I am using Firefox 2.0.0.6 on both Windows and Linux.
 
 
Just a thought but before trying to open the web page open agent switcher and choose IE 7 or whatever is offerred then open web page.  Like I said is only way I can open a bank login web page. :-k

---

### Post by Barely Here on 2008-01-05
Thank you to everyone for the suggestions and experiences. I&#8217;ve used &#8216;User Agent Switcher&#8217; add-on as suggested by Olav, and it worked well! 
[https://addons.mozilla.org/en-US/firefox/addon/59]("https://addons.mozilla.org/en-US/firefox/addon/59")

It fooled the stupid browser detection javascript, it is easy to use and passed the &#8216;usable by family&#8217; test :-) I could log into my bank account successfully.

Furthermore, it seems like my (not so nasty) email worked! HSBC has changed their whole Australian on-line banking website, and now I can successfully use my Xubuntu box to log into the on-line bank, without using the &#8216;User Agent Switcher&#8217;.

But the new web site still stubbornly lists Windows as a required Operating System. Interestingly, Mac OS X is also included in the required Operating System list; if this unix based OS can be listed as &#8216;required Operating System&#8217; why not other *nix favours? >.<

---

