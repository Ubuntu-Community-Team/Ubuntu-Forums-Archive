---
title: "No verification email from Dropbox"
date: 2014-06-21
forum: General Help
---

### Post by grey1beard on 2014-06-21
Having discovered the convenience of Dropbox(!) when family sent a link to wedding photos, I naively thought, 'that's useful - I'll have some of that'.
Downloaded the software via Ub Software Centre, and slightly miffed that the icon in the Applications menu didn't launch the programme, but pressed on, and dragged my photos of the event into my home/dp folder.
So far so good. Managed to create the account/home page, not sure how, but all the photos were there. Then tried to create a link - that seemed to work, but then I tried to copy the link to send it out to the family. 
Got a pop up asking me to click on a button to 'verify my email address', and the message changed to 'verification email sent'.
Except that it hasn't been received, not even by my junk box.
Navigated to their forums looking for solutions, but can't find any. Lots of bad vibes about support for linux, so sent a polite request to the dp support, but none yet after 3 days. 
While waiting, I thought I'd try my luck here.
Has anyone else (I'm running 12.04, on a 32 bit laptop) had a similar experience, or knows how I get over/under/round this hurdle ?
Regards,
John

---

### Post by grey1beard on 2014-06-22
This is the email that I sent Dropbox - 
> I'm running Ubuntu 12.04 LTS 32-bit, with Evolution for my mail and Firefox web browser.
I can log in ok, and have received photos via your service, but cannot share, or send a link.
I've checked for a verification mail in my junk folder and added [email]no-reply@dropbox.com[/email] to my contact list.
Nothing else I can think of that will help from my end !
Hope you can help,
Regards,
John
and this is the essential part of the reply I received this morning - 

> Dropbox Support, Jun 22 12:03 AM: 
Hi,
Thanks for writing in. While we'd love to answer every question we get, we unfortunately can't respond to your inquiry due to a large volume of support requests.

There followed several 'helpful' links, none of which cover the problem.

Please don't suggest I log into the forum, as to do that, guess what, you need to have your email verified by the same process !!!

Still hoping someone reading this might come up with a solution, as Dropbox is my preferred option (so far  ](*,) ).

John

---

### Post by Elfy on 2014-06-22
No idea if you've resent the verification mail from your posts. But [https://www.dropbox.com/help/317/en](https://www.dropbox.com/help/317/en)

---

### Post by grey1beard on 2014-06-22
Hi Elfy.
Yes, I've tried several times on each of the possible routes that prompts me for a verification - sharing, posting a link, and joining the forum, but I suspect the software uses the same route each time.
I have webmail on my isp, and I've also checked there, just in case they were blocking it, but to no avail.

John

---

### Post by Elfy on 2014-06-22
odd - not much I can say really - you'll not want to hear it worked for me I suspect. I will add that I don't actually have anything installed here, I just run .dropbox-dist/dropboxd from session startup (xubuntu)

I assume that you've checked that you've not typo'd the mail address. I assume that you're actually receiving mail at that address?

---

### Post by grey1beard on 2014-06-22
Yes, no problem with my address.
The frustrating thing is that to receive the link that lets me look at my daughter's photos, the system works, because that's how I access them, by clicking on a link sent to my email address !

John

ps I've just sent her a copy of my #2, and asked her if she could register on the Dp forum, and post the problem there.
At least I can read any replies, even if I can't ask the question.
If you're a forum member, would you care to do the same ? 
The only other thing I can think of is the uninstall/reinstall, but I'm not sure how that would make any difference. That might be a last resort move !

---

### Post by Elfy on 2014-06-22
> **grey1beard said:**
> Yes, no problem with my address.
The frustrating thing is that to receive the link that lets me look at my daughter's photos, the system works, because that's how I access them, by clicking on a link sent to my email address !

John

ps I've just sent her a copy of my #2, and asked her if she could register on the Dp forum, and post the problem there.
At least I can read any replies, even if I can't ask the question.
If you're a forum member, would you care to do the same ? 
The only other thing I can think of is the uninstall/reinstall, but I'm not sure how that would make any difference. That might be a last resort move !

I'm not a member there - I only actually got dropbox a few weeks back and have had no need.Sorry.

(I double checked my bash history - I didn't install anything from repos but did wget and untar it.)

---

### Post by grey1beard on 2014-06-22
No problem, Elfy, that's fine.
I wonder if the difference is that our distros are different, and I used the software centre ?
Outside my comfort zone, I'm afraid.
Regards
John

---

### Post by Elfy on 2014-06-22
> **grey1beard said:**
> No problem, Elfy, that's fine.
I wonder if the difference is that our distros are different, and I used the software centre ?
Outside my comfort zone, I'm afraid.
Regards
John

I think that's likely to be a red herring - your issue is with the verification itself.

---

### Post by bapoumba on 2014-06-22
Have you tried login in the web interface for both dropbox and your mail (does it have a web interface ?) instead of the clients on your machine ?
On some other site, this is what I had to do. The activation mail never ever made it to my inbox otherwise. In addition, dropbox requires you authorize the computers or phone/tablet you connect to your account. Once again, on one occasion I had to do it from the web interface, the client would not proceed.

---

### Post by grey1beard on 2014-06-22
Hi bapoumba,
My 75 year old grey cells are a bit slow here, so forgive my asking for explanations.
> **bapoumba said:**
> Have you tried login in the web interface for both dropbox ....
Is this Dropbox's own website ? The answer would be yes, and that was where I found the various links that requested I verify my email, all with the same result.

> **bapoumba said:**
> ...and your mail (does it have a web interface ?) ....

I normally use Evolution as my browser, but also have access to my mail via Easyspace.com, who are my web page provider. I've just checked again, but nothing.

> **bapoumba said:**
> 
....... In addition, dropbox requires you authorize the computers....you connect to your account. Once again, on one occasion I had to do it from the web interface, the client would not proceed.
Only using this one laptop, so I assume I'm OK there ?
Please correct me if I've misunderstood anything.

Regards
John

---

### Post by lisati on 2014-06-22
Spam/Junk folder?

---

### Post by bapoumba on 2014-06-22
No, you have not misunderstood anything :)
Other than working from websites, I have not much to recommend..
If you go to Account > Security, does it list your computer there ?

I just tried to verify my email (I guess I had neglected to do it previously, and it's been several years... :D), I received an email right away. The sender is [email]no-reply@dropbox.com[/email]. Would it be blocked in some way at easyspace ? Have you tried to check the spam folder from the easyspace web interface ? Are you positive the email in dropbox wesite is the exact same as the one (and not a variation) you use at easyspace ?

---

### Post by grey1beard on 2014-06-22
Lisati,
 Hi. Please see sentence 5 in #1.

Bapoumba.
Interesting thought, but it 'should' be covered by the fact that my easyspace site redirects all my mail to the address I'm trying to use.
However, I'll try again using the basic one registered as the my easyspace account one.
I'll also check your other suggestions.
Regards
John

---

### Post by bapoumba on 2014-06-22
> **grey1beard said:**
> 
Bapoumba.
Interesting thought, but it 'should' be covered by the fact that my easyspace site redirects all my mail to the address I'm trying to use.
However, I'll try again using the basic one registered as the my easyspace account one.
I'll also check your other suggestions.
Regards
John

Yes and no. I used to redirect another email to gmail. Spam mails that got caught by this other email provider did not get forwarded. So it might be interesting to log into the web interface of the email provider you used with dropbox. Last thought, but unlikely, would you been using rules or filters from noreply@ for ex ?

---

### Post by grey1beard on 2014-06-22
No luck with my email provider, and regarding the noreply address, I merely added that to my address book, without using  any additional rules or filters. 
So unless the dropbox forum come up with a solution, it might be the reinstall route.
But only when I've finished the ironing !

John

---

### Post by bapoumba on 2014-06-22
Last thought : create another account with dropbox. If your current account is borked in some way with them, it may be difficult to troubleshoot. You'll need another email that has never been registered on their website though.

---

### Post by grey1beard on 2014-06-22
Thanks for your help, and I'll give that a shot this afternoon. If it solves the problem I'll post back here.
Au revoir,
John

---

### Post by buzzingrobot on 2014-06-22
I'll guess you've been thru the verification drill here:  [https://www.dropbox.com/help/317/en](https://www.dropbox.com/help/317/en) ?

---

### Post by Elfy on 2014-06-22
> **buzzingrobot said:**
> I'll guess you've been thru the verification drill here:  [https://www.dropbox.com/help/317/en](https://www.dropbox.com/help/317/en) ?
post #3 :)

---

### Post by grey1beard on 2014-06-22
hi buzzingrobot, and yes, that was the first thing I did.
W hen I click on it, it displays the message ' verification email sent'
Trouble is it never arrives !
John

---

### Post by grey1beard on 2014-06-22
Just visited the latest reviews on Ubuntu Sftware centre, and noticed all bad since the middle of January this year. Three of the four actualy indicate a change, OK before, now bad.
Not good news.

---

### Post by grey1beard on 2014-06-22
So, I changed my email to the catchall address that I have, but that made no difference.
I uninstalled it via synaptic, and reinstalled via the software centre. Interestingly, it had my changed email address showing when I ran the software, and it didn't ask me to log in.
If this is the case, one might wonder why it needs to verify my email address !
Still, I pushed on to 'share a link', and it then told me it had sent a verification email.
But alas, nothing arrives.

I wonder if it might be worth uninstalling again, via the software centre, then using terminal to install ?

---

### Post by bapoumba on 2014-06-22
I'd personally do the registration procedure over from the website and not from the client. Other than that, no other suggestion :(

---

### Post by grey1beard on 2014-06-22
Final ignominy. Even though I've deleted the software, as soon as I go to the dropbox site, I'm signed in and all my files are still there.
So next I need to delete my files and wave dropbox goodbye before I can make a fresh start. 
Or perhaps not bother, and try Copy instead ?

John

---

### Post by bapoumba on 2014-06-22
> **grey1beard said:**
> Final ignominy. Even though I've deleted the software, as soon as I go to the dropbox site, I'm signed in and all my files are still there.
So next I need to delete my files and wave dropbox goodbye before I can make a fresh start. 
Or perhaps not bother, and try Copy instead ?

John
You probably have checked the remember me box. You'd need to clear dropbox cookies from your browser to be logged out.

---

### Post by grey1beard on 2014-06-22
Thanks again.

I think I'm getting a headache. Time for a strong mug of the best !
John

---

### Post by buzzingrobot on 2014-06-22
Dropbox won't delete your files on its servers until you wipe out the account.  

I remember Dropbox issues --not verification -- when I ran 12.04 and installed Dropbox from the repos. When I installed from the Dropbox site, all was well.  

I suppose, too, that there's a slim chance that Dropbox had a problem generating that email.

---

### Post by grey1beard on 2014-06-22
Well, I've managed to clear dropbox1, and have started again.
Followed the instructions on their site, I've used terminal to download and install the dropbox folder.

However the last instructions - *Download this CLI script to control Dropbox from the command line.* I've done, and the dropbox.py script is in my home folder, but left my terminal hanging with a new line */usr/bin/nautilus * and terminal not going anywhere.
Also I note that there's no menu in Appplications this time, presumably because I used a cli to install the software.
Is that what the final instruction -  *For easy access, put a symlink to the script anywhere in your PATH.* is about ?
If so I'll need a hint on that !
I recognise the words, but only have a vaque idea on what I need to do, but none on how to do it.

---

### Post by buzzingrobot on 2014-06-22
> **grey1beard said:**
> Well, I've managed to clear dropbox1, and have started again.
Followed the instructions on their site, I've used terminal to download and install the dropbox folder.

However the last instructions - *Download this CLI script to control Dropbox from the command line.* I've done, and the dropbox.py script is in my home folder, but left my terminal hanging with a new line */usr/bin/nautilus * and terminal not going anywhere.
Also I note that there's no menu in Appplications this time, presumably because I used a cli to install the software.
Is that what the final instruction -  *For easy access, put a symlink to the script anywhere in your PATH.* is about ?
If so I'll need a hint on that !
I recognise the words, but only have a vaque idea on what I need to do, but none on how to do it.

Is this how you installed? ```

cd ~ && wget -O - "https://www.dropbox.com/download?plat=lnx.x86" | tar xzf -


~/.dropbox-dist/dropboxd

```

I've done that several times and never had a reason to install the CLI script.  That script, I believe, is intended for admins and such who don't use a GUI interface and need to control Dropbox strictly from the command line.

"~/.dropbox-dist/dropboxd"  will display Dropbox's signon/get new account panel if it thinks it's a brand new install. Once logged in, you should see Nautilus open and the Dropbox folder begin to populate, and the little blue Dropbox icon should appear in the panel.

With this approach, you do need to launch "Startup Applications" and manually add Dropbox, so it runs every time you restart or logoff and back in. The command you want to enter should be like this "/home/YourUserName/.dropbox-dist/dropboxd".

---

### Post by grey1beard on 2014-06-22
Yes, that's what I did.
Thanks for the explanation, and the extra instructions.
Nice to have friends pushing you up the learning curve.
Regards
John

---

### Post by grey1beard on 2014-06-22
Observations.
When I went to startup applications, Dropbox was already there, presumably from the previous incarnation.
So I deleted it, and re-booted. Then I added it, along with the command, and again re-booted.
There is no sign of the prog in Applications, no icon on the top task bar, so I dragged a single photo onto the home/Dropbox folder, then going to the web page to 'sign in', the page immediately shows the files that I merged from the previous installation, plus the new one that I added.
So far, so reasonably good.
However, sharing a link and trying to get a verification email from them is exactly the same.

So in spite of your valient efforts on my behalf, I'm back, like Sisyphus, at the bottom of the hill.

At least it doesn't go on for ever. I can give up ?

John

---

### Post by Elfy on 2014-06-22
Odd - I wonder whether you'd get mileage talking to easyspace - perhaps something is awry there - and if you pay them I'd guess they've got a proper support system for you, rather than trying to get help from dropbox.

---

### Post by grey1beard on 2014-06-22
Many many thanks, Elfy, you've cracked it !

I didn't get as far as talking to anyone at easyspace, but I did have a thorough dig through my email security settings, a place I'd not been to before.
In particular the Spam filters. 
Because there is a spam folder on my webmail page, I had wrongly assumed that any spam received would be displayed there. My bad.
It went under the radar that there never had been anything displayed in the spam folder, and I didn't see the significance of that.
I finally found(no, tripped over would be more accurate) a path to the spam filter settings, white list and black list etc.
Fortunately I had tried the dropbox link only moments before, and there it was, heading the list as the latest spam that they had protected me from.

Transferred to the white list, clicked on the link back, and away we go.

Many thanks to all who have kept me going,

John

---

### Post by Elfy on 2014-06-22
Excellent - glad to see you persevered with it :)

---

