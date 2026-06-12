---
title: "Tor | Networking | Chosing exit nodes - fails |"
date: 2022-01-10
forum: General Help
---

### Post by noobtechninja on 2022-01-10
[SUP]&#8203;[/SUP]Hi there guys.

I was hoping that you could help answer a couple of queries for me please.


Issue / background:
I'm starting to tinker with Tor, and learn some more elements of secure 
networking.


I want to chose a specific exit node for some testing.
(I'd like the exit point to be in the UK, for this test).


However, when I edit the torc config file, Tor will attempt to launch
then fail with the following error message:


```

Tor exited during startup. This might be due to an error in your torrc file, a 
bug in Tor or another program on your system, or faulty hardware. Until you fix 
the underlying problem and restart Tor, Tor Browser will not start.
```


I have been following the guide below:
[https://www.wikihow.com/Set-a-Specific-Country-in-a-Tor-Browser](https://www.wikihow.com/Set-a-Specific-Country-in-a-Tor-Browser)

Here is an example of the entry and exit nodes on the torc config file
that I was testing:
```
 EntryNodes {ca} StrictNodes 1
ExitNodes {uk} StrictNodes 1 
```


Troubleshooting steps:

1. I've tried to use both lowecase and uppercase for the country codes
in the curly brackets.

2. Use both 1 & 0 for the StrictNodes argument

3. Tried different countries in both the entry and exit nodes
E.G. {US} {FR} {NL}

Nothing seems to work. Tor will fail to launch properly.
(Just showing the error message).

4. However, once I delete my changes, and re-save the torc config file.
Tor will launch properly once again.


Questions:
Q1. What am I doing wrong ?
Q2. What do I need to do, in order to get this to work, please ? 


TIA for any help or advice.


Useful details
Tor version: 11.03 (based upon Firefox 91.4.1.esr (64-bit) )

---

