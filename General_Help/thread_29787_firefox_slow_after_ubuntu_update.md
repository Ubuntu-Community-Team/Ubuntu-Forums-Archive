---
title: "firefox slow after ubuntu update"
date: 2005-04-25
forum: General Help
---

### Post by bennettg on 2005-04-25
nOOb here.....now almost 99.9% of m$.

was using suse but tried ubuntu for synaptic.  used ubuntu update manager last night when promoted to upgrade packages (including gimp).  since that time, firefox is so SLOW.  not dsl problem as windows is working just fine.  tried mozilla 1.7 and had same problems.

i have followed the directions to increase speed found on ubuntuguide.org

is anyone else experiencing this?   thanks

---

### Post by bored2k on 2005-04-25
Did you disable ipv6 in about:config ?

---

### Post by bennettg on 2005-04-25
yes i did.  i followed the instructions at ubuntuguide.org

also if it helps.....when it is slow, it always says "looking up www.xxxxxxx.com" in the lower left corner of fireofx

why is this happening?  ubuntu was great until i ran the update and this happened

---

### Post by bennettg on 2005-04-25
also, if helpful:

the speed seems to increase once a gien website is loaded.  for example, while it takes a long time to load [www.qwest.com](www.qwest.com), after it loads the links on the site load quickly.

is this a proxy issue?

---

### Post by DutchLau on 2005-04-26
Maybe something happened that it's preloading the whole website? That would explain why it's so slow. - I always give a fresh install of any operating system (less quirks when it's done installing :) )

---

### Post by 12quality on 2005-05-01
I had the same problem forever.  Everybody suggested disabling IPv6, but this was not my problem.  I have seen a ton of posts with my problem where disabling IPv6 didn't solve it, so this is a separate but very common problem.

It happenned to me in both Warty and  in Hoary.  I was running a dual boot with XP and I had no problems in XP, but Ubuntu web surfing was so slow,  Warty would say **Resolving Host [website] ...** and Hoary would say **Looking up [website] ...**.  But it was not just Firefox, the whole system was slow at DNS lookup.

One unique thing that we both witnessed was that it would take forever to load a webpage, but once there, you could zoom from page to page on that site.  This is because it was taking forever to look up the ip address from the name of the site.  Once it did this, your browser no longer needed to keep looking up the address.  

Here's the solution.  Change your DNS server.  **Go to System-> Administration->Networking.  Click on the DNS Tab.  Under DNS Servers, delete what's there and replace it with a better server.**  I'm no expert on which to use, but I just found one close by at GaTech (130.207.165.170) and now Firefox is faster than it was on XP.

A few comments: 
1) I have a Netgear router connected to my cable modem.  If you do too, may be this is the issue.  I also use Charter High Speed, Could this be it?
2) My system still sometimes inexplicably switches back to the old DNS server addresses.  I tried to save the specified DNS server address in a new profile, but the system often goes back to the default unnamed profile.  I changed the Server addresses in this profile, too, but it will still sometimes lapse into using the automatically generated  addresses.  How do I make it stay with the DNS servers I want?

---

