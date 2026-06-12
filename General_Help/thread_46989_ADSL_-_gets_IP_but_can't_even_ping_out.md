---
title: "ADSL - gets IP but can't even ping out"
date: 2005-07-06
forum: General Help
---

### Post by taryneast on 2005-07-06
Hi, I really need some help on this as it's been driving me insane.

I've had this problem about 4 or 5 times now. The ADSL goes down for some reason (blackout or kernel upgrade or whatever) and when it all comes back up - no go on the adsl. This is despite the fact that nothing has changed in the config files afaik (eg the power outages wouldn't have done so - oh and yes, I have a surge protector, on the phone lines as well as power - I don't think that's the problem).

What has happened in the past is that it stays down for a few days to a week, then magically comes back up again all by itself.

Now this issue isl compounded by the fact that I don't fully grok how it all really works - I have a small selectiuon of dead chickens and rain dances, which I tend to do to find out what's going on, but none of them do much in this instance.

When this problem occurs, I start with ifup eth0 - which tells me it's happily configured already. I try ifconfig eth0 and it gives a sensible IP (it even changed all by itself last week (while the adsl was not working) to another sensible IP - which is what happens when it is normally working ok). I can ping this IP and it works. I use netstat -rn to find the gateway I'm supposed to be talking to - I try to ping that but that doesn't work (nor do any other IPs that I try - and of course DNS isn't there cos I can't get "out"). I have gone to 192.168.0.1 in my browser and disconnected/reconnected the modem and it tells me it's happily connected.

as far as I can tell using the limited knowledge I have it's all ok... except that nothing internetty is working.

I have tried stuff like power cycling, (incuding the modem, and including in different timing - eg wait for the modem first, wait unti lthe computer has loaded, then cycle the modem etc), I've looked in my various crontabs to see if there is anything regular that could be what brought it back up again the other times (not hthat I can see, but I don't know what I'm looking for). I've even resorted to randomly running any script in /ppp or beginning with "dhc..." none of which seems to have done the trick...

I would appreciate *any* help that anyone can give as I'm desperate - this is getting me very depressed. This time it's been down for almost two weeks and hasn't shown any signs of magically resurrecting itself - and really I'd prefer to be able to figure out what's actually wrong with it rather than pointing bones and shaking...

I'm currently emailing from work so I apologise if turn-around time for any answers from me will be slow - I beg your indulgence. Also, any information will be just whatever I can go and write down on paper and bring back here - obviously I can't cut/paste error messages etc as I can't get anything useful from there to here any other way atm.

Please help.
Taryn

PS - I put this is "installation help" forum too - not sure if this is an install problem or an "application" problem... many apologies in advance for both cross-posting and possibly incorrect categorisation

---

