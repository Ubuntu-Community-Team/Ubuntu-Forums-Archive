---
title: "You tube on and off connection on 15.04"
date: 2015-05-23
forum: General Help
---

### Post by bill83 on 2015-05-23
Hey folks; I'm very new here. Been using Ubuntu for about 3-4 months. Am on 15.04 at the moment. In general things have been good,,i'm a simple user. One of the things that has me scratching my head is that for the last month i keep losing and then gaining back my you tube connection. When i first lost it i searched around here for answers and thought that that i had lost support on FireFox for YT. I had Chrome and proceeded to install Pepperflash.  YT was restored on Chrome, but also on FF,,what?. Hey if its working, good. Since then YT has come and gone a few times so i'm here hoping for an answer or something to check out. 
15.04 is on an Acer Aspire 2920 laptop.
Intel 2 duo cpu Ts450 at 1.66 ghzx2
Also intel 965GMx86 /MMX/SSE2

Not sure what other info to give
Thanks ahead of time for any help you can offer.
BTW, i like Ubuntu

bill

---

### Post by Vladlenin5000 on 2015-05-24
Just a couple of preliminary notes:

1. YouTube no longer requires Flash to work. YT, Vimeo and hundreds of others already moved to HTML5
2. Google **Chrome** already has everything you need: Default is also HTML5 but it has also the latest Flash. **Chromium**, the open source project Chrome is based on and the only one available at Ubuntu repositories also defaults to HTML5 but doesn't contain the Flash.

Now, can you please explain what you mean by "loosing Youtube" or "YT has come and gone?
Is it some third-party app you're using? If so, the reason has been explained in the other thread where you posted. But is it really the some issue or similar? If not then there's no point in your other post, it's "thread hijacking" and quite frown upon almost anywhere.

---

### Post by bill83 on 2015-05-24
Vlad; to answer your question, "youtube on and off", when i do a normal google search for youtube or try to watch a youtube video on any particular site i get a message that firefox can't find the server; I can watch vimeo and cellphone video's though. For some reason i can't get youtube. Chrome says "the page is not available". Now this situation comes and goes. Its the intermittent accessibility that has me scratching my head. I realize this isn't a flash issue and i'll go find that other thread to see what i missed.

---

### Post by Vladlenin5000 on 2015-05-24
Quite unusual...

Youtube is a website like any other. Are you saying that all the other websites you visit load properly yet Youtube at the some time doesn't? Does it also happen when you go directly to Youtube.com and play (or try to) any video?

---

### Post by monkeybrain20122 on 2015-05-24
Firewalled?

---

### Post by bill83 on 2015-05-24
> **Vladlenin5000 said:**
> Quite unusual...

Youtube is a website like any other. Are you saying that all the other websites you visit load properly yet Youtube at the some time doesn't? Does it also happen when you go directly to Youtube.com and play (or try to) any video?

That's correct. All my other websites work fine. I can't get access to play a youtube video in any way , or by going direct to youtube.com. I'm on facebook as part of a music community so there are video's that come up all the time. Vimeo plays as does cellphone vid's , but youtube, zip. Its strange. I don't really know what to look for as i don't know the os or the pc well. I'm coming from a decade on a mac. Any other suggestion would be welcome.

---

### Post by Vladlenin5000 on 2015-05-25
Nothing to do with the PC or OS, apparently.

Where are you connecting from? Home or work/school? I'm starting to suspect post#5 by monkeybrain20122 is indeed in the right track...
Have you tested other computers using the exact same internet connection?

---

### Post by bill83 on 2015-05-25
> **Vladlenin5000 said:**
> Nothing to do with the PC or OS, apparently.

Where are you connecting from? Home or work/school? I'm starting to suspect post#5 by monkeybrain20122 is indeed in the right track...
Have you tested other computers using the exact same internet connection?

I'm connecting from home.As far as i can see there is no firewall. I still have the mac hooked up and it works fine as does youtube on the Mac.

Addition to the above; both mac and pc are on a router. I looked on the router and there is a firewall. I disabled it and tried to connect to YT,,wouldn't connect.

---

### Post by mc4man on 2015-05-25
Can you log out  & log into a guest session. Then use this address - does FF work?, if not take a screenshot of the FF window & attach to post, use Manage Attachments in reply window
(- with FF in focus go alt+PrtSc or whatever the print screen button is to take a screenshot

[https://www.youtube.com/](https://www.youtube.com/)

---

### Post by bill83 on 2015-05-25
Here is the screenshot. I couldn't get the screenshot to happen but here's a pic of it on flickr

[https://flic.kr/p/th5jXC](https://flic.kr/p/th5jXC)

---

### Post by bill83 on 2015-05-25
Also a tech friend of mine found this. I know it has to  do with flash but i wonder if permissions have anything to do with it.

  "This is a weird possibility but is your flash grabbing a sound card?  Flash will show some things normally but will stop working if it cannot  find what sound card you are using. If your aplay -l output from terminal is not listing anything, then there is no soundcard to grab. If your sudo aplay -l gives you an output, then you have user/group permissions to configure. Hope this helps."

---

### Post by mc4man on 2015-05-25
So you are saying that if right now you scroll up to post 9 &   click on the link you get a Server not found page?

---

### Post by bill83 on 2015-05-25
> **mc4man said:**
> So you are saying that if right now you scroll up to post 9 &   click on the link you get a Server not found page?

That's correct.

---

### Post by mc4man on 2015-05-25
> **bill83 said:**
> That's correct.
Well then no clue here, you also tried the link in post 9  in a guest session?
What's confusing about your picture (screenshot) is it shows an extended url or part of , not just youtube's  main page.
(as in this is showing which is just a 404 here - [https://www.youtube.com/results/search_query=mbira](https://www.youtube.com/results/search_query=mbira)

---

### Post by bill83 on 2015-05-25
> **mc4man said:**
> Well then no clue here, you also tried the link in post 9  in a guest session?
What's confusing about your picture (screenshot) is it shows an extended url or part of , not just youtube's  main page.
(as in this is showing which is just a 404 here - [https://www.youtube.com/results/search_query=mbira](https://www.youtube.com/results/search_query=mbira)

If you mean by"guest session", being "logged out", then yes its the same result.

---

### Post by Vladlenin5000 on 2015-05-25
Well, logging out of your regular user's session then logging in again as guest (without password). By default standard Ubuntu has the guest session enabled; I don't know about other flavors.
And please check whether or not something changes in the URL when you either click on the link in the post #9 or type [www.youtube.com](www.youtube.com) directly. Either way it shouldn't change to/add anything else after the .com... If it does then you have some sort of re-direction that can come from some add-on or something else.

The URL you shown us does indeed result in a 404. Just out of curiosity I tried to search "mbira" in Youtube (as a regular non-logged user) and the resulting URL was [https://www.youtube.com/results?search_query=mbira](https://www.youtube.com/results?search_query=mbira) . Notice the difference?
Aren't you by any chance clicking in some (wrong) link instead of the one we repeatedly ask you to try, the main Youtube website? The one you're showing couldn't possibly work. I haven't noticed it at first glance but now it's obvious it won't work no matter what.

---

### Post by mc4man on 2015-05-25
Yeah, that was a typo in my typing here & the  reply, seems I used  / instead of ?  like in the screenshot. 
(which does produce a page though the point before was to try a fresh FF config/cache, ect. (guest) & just go to the main page.
Anyway a curious matter...

---

### Post by bill83 on 2015-05-25
> **Vladlenin5000 said:**
> Well, logging out of your regular user's session then logging in again as guest (without password). By default standard Ubuntu has the guest session enabled; I don't know about other flavors.
And please check whether or not something changes in the URL when you either click on the link in the post #9 or type [www.youtube.com]("http://www.youtube.com") directly. Either way it shouldn't change to/add anything else after the .com... If it does then you have some sort of re-direction that can come from some add-on or something else.

The URL you shown us does indeed result in a 404. Just out of curiosity I tried to search "mbira" in Youtube (as a regular non-logged user) and the resulting URL was [https://www.youtube.com/results?search_query=mbira](https://www.youtube.com/results?search_query=mbira) . Notice the difference?
Aren't you by any chance clicking in some (wrong) link instead of the one we repeatedly ask you to try, the main Youtube website? The one you're showing couldn't possibly work. I haven't noticed it at first glance but now it's obvious it won't work no matter what.

I wasn't really noticing the extension but when you mentioned mbira i thought "What"?. I have a bookmark to go to a search for mbira video's on youtube . I may have used it for the pic but i definitely was cliking the #9 post and also typing [www.youtube.com](www.youtube.com) in the google url box.   So i deleted the bookmark and one other unsorted youtube bookmark and now the extension is gone,,,BUT,,,,,that's all. I'm still getting the same message. The url box has no estension but i'm getting the same message.

---

### Post by mc4man on 2015-05-25
For curiosity try this, would be good to do exactly -
open a terminal (ctrl+alt+t 
copy & paste this in, press enter on keyboard
```
firefox -private-window 
```
In the FF window that opens just type this into the address bar , press enter
```
youtube.com
```
(it's likely to offer an autocomplete dropdown after you have typed 'you', you can use the  top choice  or just type out  as above
What happens?

edit:
Too bad can't seem to combine -private-window  & --safe-mode ? but try anyway as above. You could also try the same with 
firefox --safe-mode

---

### Post by bill83 on 2015-05-25
> **mc4man said:**
> Yeah, that was a typo in my typing here & the  reply, seems I used  / instead of ?  like in the screenshot. 
(which does produce a page though the point before was to try a fresh FF config/cache, ect. (guest) & just go to the main page.
Anyway a curious matter...

So i do not see a guest option. The only thing i'm seeing is a button on the upper right saying "loggin with SSO". .I don't see any other option. As you might have read in my previous post i may have taken the pic from the bookmark link but it doesn't change anything .Anyway it remains a curious and annoying problem .

---

### Post by Vladlenin5000 on 2015-05-25
Well well well... The plot thickens :???:

One quite far-fetched possibility is a specific rule blocking YT for that machine only at the router/gateway. Not that difficult in most routers. Even consumer grade (SOHO) small routers from 10 years ago could do it with the original firmware. With DD-WRT, OpenWRT or Tomato you can easily do that and much more.

Update:
Somehow I've missed the post #19. Please try. It's a brilliant idea.

---

### Post by bill83 on 2015-05-25
> **mc4man said:**
> For curiosity try this, would be good to do exactly -
open a terminal (ctrl+alt+t 
copy & paste this in, press enter on keyboard
```
firefox -private-window 
```
In the FF window that opens just type this into the address bar , press enter
```
youtube.com
```
(it's likely to offer an autocomplete dropdown after you have typed 'you', you can use the  top choice  or just type out  as above
What happens?

edit:
Too bad can't seem to combine -private-window  & --safe-mode ? but try anyway as above. You could also try the same with 
firefox --safe-mode

I tried the private window in terminal etc,,,,,,,,,same result, but thanks for trying to solve my problem.

---

### Post by bill83 on 2015-05-25
> **Vladlenin5000 said:**
> Well well well... The plot thickens :???:

One quite far-fetched possibility is a specific rule blocking YT for that machine only at the router/gateway. Not that difficult in most routers. Even consumer grade (SOHO) small routers from 10 years ago could do it with the original firmware. With DD-WRT, OpenWRT or Tomato you can easily do that and much more.

Update:
Somehow I've missed the post #19. Please try. It's a brilliant idea.

The router is an older one from a friend. I'm not sure how old,,,,,, but youtube was working last week and i've had the router on here for months.

---

### Post by Vladlenin5000 on 2015-05-25
> **bill83 said:**
> The router is an older one from a friend. I'm not sure how old,,,,,, but youtube was working last week and i've had the router on here for months.

The age of the router doesn't matter. I just mentioned those from 10 years ago to explain this isn't a "new thing" either. And it's easy to do if you know how.
I did it once just for fun, here's the story:
Summer 2005 - I was in [somewhere in Spain] with a group of friends in a rented flat with cable service but with a cable-modem only. So, they asked the 'nerd' to bring a router so we all could have access. Normal setup in the first and everything working as expected. Then, the next day, I added a few rules blocking MSN to all but me :mrgreen:... Yeah... It was just for fun and watch them cursing, then punching the furniture and their own laptops, then cursing again... Lots of fun!

So...
I would check it anyway and certainly rebooting the router itself won't hurt.

---

### Post by mc4man on 2015-05-25
The other thing to try would be to move ~/.mozilla to a .bak **with FF closed,** then open for a fresh one.  If inclined - 
in a terminal -
```
mv ~/.mozilla  ~/.mozilla.bak
```
Then open FF & try again, don't accept any offer to import if it comes up.

---

### Post by bill83 on 2015-05-26
> **Vladlenin5000 said:**
> The age of the router doesn't matter. I just mentioned those from 10 years ago to explain this isn't a "new thing" either. And it's easy to do if you know how.
I did it once just for fun, here's the story:
Summer 2005 - I was in [somewhere in Spain] with a group of friends in a rented flat with cable service but with a cable-modem only. So, they asked the 'nerd' to bring a router so we all could have access. Normal setup in the first and everything working as expected. Then, the next day, I added a few rules blocking MSN to all but me :mrgreen:... Yeah... It was just for fun and watch them cursing, then punching the furniture and their own laptops, then cursing again... Lots of fun!

So...
I would check it anyway and certainly rebooting the router itself won't hurt.

A friend of mine whose in the IT industry checked out the router last night. Its ok, But thanks for the suggestion.

---

### Post by bill83 on 2015-05-26
> **mc4man said:**
> The other thing to try would be to move ~/.mozilla to a .bak **with FF closed,** then open for a fresh one.  If inclined - 
in a terminal -
```
mv ~/.mozilla  ~/.mozilla.bak
```
Then open FF & try again, don't accept any offer to import if it comes up.

BINGO; so that seems to have fixed the problem. I'm now getting youtube. So a big thumbs up to you mc4man. The question i have though is what did this change do. I notice that i have no bookmarks , not a big deal. Just curious where am i now in mozilla or FF.
bill

---

### Post by mc4man on 2015-05-26
> **bill83 said:**
> BINGO; so that seems to have fixed the problem. I'm now getting youtube. So a big thumbs up to you mc4man. The question i have though is what did this change do. I notice that i have no bookmarks , not a big deal. Just curious where am i now in mozilla or FF.
bill
You are just starting off with a fresh FF profile & using the default settings. So you can add back the Bookmarks Toolbar & populate it ect.
You must have had either some setting or something messed up so now you're back to new.
(- this is what FF in a guest session would have had & would have worked. Why that session isn't available no idea, a bit of a moot point in this regard.

---

### Post by bill83 on 2015-05-26
Thanks again Mc4man, i appreciate it.

---

### Post by Vladlenin5000 on 2015-05-26
The mystery is finally solved, the culprit has been caught and like in many stories, the first suspect was the guilty one but we had to go full circle ;)

Now it's time for you to relax and enjoy your new OS. Happy Ubuntuing. :guitar:
Come back if you need something else or just to chat at The Café (yes, this is the correct spelling).

---

### Post by bill83 on 2015-05-28
Well this is annoying. The problem has returned. I'm getting the same window as before.

---

### Post by bill83 on 2015-05-29
So last night i found "guest session" that MC4man was trying to get me to do. Seeing as the problem had come back, that being that i can't connect or watch youtube video's, i decided to go into guest session and bring up YT, which it did, and then i closed everything, went into normal session, and now i can get YT. So the question is why is this happening. Why after a couple of days is there a disconnect.

---

### Post by bill83 on 2015-05-31
So I'm back to no YT again , now going into guest session doesn't do anything so i'm thinking that the one time it seemed to fix the problem was a coincidence. As much as i like linux i'm starting to get to the place where if i can't have basic functioning then why bother.

---

