---
title: "[Worked around] Firefox just disabled my addons (just me?)"
date: 2019-05-03
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2019-05-03
I had to set the config option [FONT=courier new]xpinstall.signatures.required[/FONT] to [FONT=courier new]false[/FONT] get it working again
[ATTACH=CONFIG]283177[/ATTACH]

---

### Post by DuckHook on 2019-05-03
You're a life-saver pqwoerituytrueiwoq.

No, it's not just you. I've been trawling the net with growing desperation looking for a solution and should have known that an expert on this very forum would have one.

What concerns me is that it went off like a time bomb. Hundreds of complaints on Reddit and elsewhere, all within the last few hours. It's like FF devs wrote a routine into the browser so that, come UTC XX:XX, FF would blow up in our faces.

Makes me question the advisability of relying on it as my main browser. :-k

What is actually happening???

---

### Post by #&amp;thj^% on 2019-05-03
> **DuckHook said:**
> You're a life-saver pqwoerituytrueiwoq.


What is actually happening???

+1
But if your not adding new addons and stay/re-enable with the old already trusted ones, should be good for now anyway. :)
Wanted to add this for your reading pleasure: [https://wiki.mozilla.org/Addons/Extension_Signing](https://wiki.mozilla.org/Addons/Extension_Signing)

---

### Post by Bashing-om on 2019-05-03
Hey all -

Here:
[https://bugzilla.mozilla.org/show_bug.cgi?id=1548973](https://bugzilla.mozilla.org/show_bug.cgi?id=1548973)
< ubottu> Mozilla bug 1548973 in Add-ons Manager "All extensions disabled due to expiration of intermediate 
                signing cert" [Blocker,New]

Good thing is that Mozilla is aware - would have been nice to have had some warning.

---

### Post by Skaperen on 2019-05-04
this was happening to me but it quit after doing **[FONT=courier new]apt-get dist-upgrade[/FONT]** and rebooting about half an hour ago.

---

### Post by cruzer001 on 2019-05-04
Fairly fresh install of FF60 ESR also affected, has no addons.

---

### Post by nubbe on 2019-05-04
Awesome! Thanks!

---

### Post by monkeybrain20122 on 2019-05-04
Mozilla fixed it on its end, it is working now.

---

### Post by DuckHook on 2019-05-04
> **Bashing-om said:**
> Hey all -

Here:
[https://bugzilla.mozilla.org/show_bug.cgi?id=1548973](https://bugzilla.mozilla.org/show_bug.cgi?id=1548973)
< ubottu> Mozilla bug 1548973 in Add-ons Manager "All extensions disabled due to expiration of intermediate 
                signing cert" [Blocker,New]

Good thing is that Mozilla is aware - would have been nice to have had some warning.

Further to Bashing-om's link (thanks for that, BTW), and specifically, this statement: [https://bugzilla.mozilla.org/show_bug.cgi?id=1548973#c57](https://bugzilla.mozilla.org/show_bug.cgi?id=1548973#c57)
>  Eric Rescorla (:ekr)
	
Comment 57 &#8226; 7 hours ago

Update: We have rolled out a partial fix for this issue. We generated a new intermediate certificate with the same name/key but an updated validity window and pushed it out to users via Normandy (this should be most users). Users who have Normandy on should see their add-ons start working over the next few hours. We are continuing to work on packaging up the new certificate for users who have Normandy disabled.
&#8230;and this:
> 
	Sylvestre Ledru [:sylvestre]
	
Updated &#8226; 6 hours ago
Summary: [work in progress] All extensions disabled due to expiration of intermediate signing cert &#8594; [first mitigation completed, working on a second one] All extensions disabled due to expiration of intermediate signing cert&#8230;and this:
> 
	Russell Odom
	
Comment 60 &#8226; 6 hours ago

For everyone's info: we don't need to so anything if ""studies" is enabled (Firefox Preferences -> Privacy & Security -> Allow Firefox to install and run studies).

See [https://discourse.mozilla.org/t/certificate-issue-causing-add-ons-to-be-disabled-or-fail-to-install/39047/12](https://discourse.mozilla.org/t/certificate-issue-causing-add-ons-to-be-disabled-or-fail-to-install/39047/12)

Just for kicks and giggles, I tried reverting the toggle in the [FONT=Fixedsys]xpinstall.signatures.required[/FONT] to [FONT=Fixedsys]false[/FONT] just now, and no go. It's still broken/workaround still needed.

FYI: I do not have "studies" enabled. It's part of my standard browser lockdown and I'm not sure why anyone would unless they were Mozilla testers or such.

---

### Post by DuckHook on 2019-05-04
> **monkeybrain20122 said:**
> Mozilla fixed it on its end, it is working now.
Not on my browser it isn't. FF 66.03

---

### Post by donbcilly on 2019-05-04
It fixed itself after about an hour in mine (66.03).

---

### Post by scriber on 2019-05-04
[https://blog.mozilla.org/addons/2019/05/04/update-regarding-add-ons-in-firefox/](https://blog.mozilla.org/addons/2019/05/04/update-regarding-add-ons-in-firefox/)

---

### Post by pqwoerituytrueiwoq on 2019-05-04
for me i am able to set the workaround setting to true and it works fine
* i do happen to have studies enabled

---

### Post by monkeybrain20122 on 2019-05-04
> **DuckHook said:**
> Not on my browser it isn't. FF 66.03

Yeah strange isn't it? I have two Ubuntu installations, 16.04 on one machine and 18.04 on the other. Both have FF66.03 and same addons. On the 16.04 machine FF never has a problem at all, everything works as it should. But FF in Ubuntu 18.04 got hit by this some times after midnight When that happened I did something, including reboot the 16.04 machine to see if the same thing happened to FF there too, but nothing, it was normal .. Then a few hours ago FF in 18.04 fixed itself, no more problem...

---

### Post by Rubi1200 on 2019-05-04
Happened to me too but seems to have resolved itself now without further action.

---

### Post by DuckHook on 2019-05-04
> **scriber said:**
> [https://blog.mozilla.org/addons/2019/05/04/update-regarding-add-ons-in-firefox/](https://blog.mozilla.org/addons/2019/05/04/update-regarding-add-ons-in-firefox/)

> **pqwoerituytrueiwoq said:**
> for me i am able to set the workaround setting to true and it works fine
* i do happen to have studies enabled
Having studies on seems to be the magic trick. On my VMs where studies is left on FF as per default, they are fixed. On my bare-metal install where I have reporting to Mozilla off, I still must use the workaround.

To be honest, I'm not sure how I feel about either method. Decisions, decisions…

---

### Post by #&amp;thj^% on 2019-05-04
> **DuckHook said:**
> Having studies on seems to be the magic trick. On my VMs where studies is left on FF as per default, they are fixed. On my bare-metal install where I have reporting to Mozilla off, I still must use the workaround.

To be honest, I'm not sure how I feel about either method. Decisions, decisions&#8230;

Just to add to your dilemma: Until a fix is out for all, you can temporarily re-enable all extensions by opening **about:config**, **setting devtools.chrome.enabled to true**, and then opening the JS dev console by pressing "Ctrl+Shift+J" and executing the following code in the console[4]:
```

// Re-enable *all* extensions

    async function set_addons_as_signed() {
        Components.utils.import("resource://gre/modules/addons/XPIDatabase.jsm");
        Components.utils.import("resource://gre/modules/AddonManager.jsm");
        let addons = await XPIDatabase.getAddonList(a => true);

        for (let addon of addons) {
            // The add-on might have vanished, we'll catch that on the next startup
            if (!addon._sourceBundle.exists())
                continue;

            if( addon.signedState != AddonManager.SIGNEDSTATE_UNKNOWN )
                continue;

            addon.signedState = AddonManager.SIGNEDSTATE_NOT_REQUIRED;
            AddonManagerPrivate.callAddonListeners("onPropertyChanged",
                                                    addon.wrapper,
                                                    ["signedState"]);

            await XPIDatabase.updateAddonDisabledState(addon);

        }
        XPIDatabase.saveChanges();
    }

    set_addons_as_signed();

```
Due to the nature of this I felt it was safe to share. [https://wiki.archlinux.org/index.php/Firefox#Firefox_disables_all_extensions_due_to_Mozilla_not_renewing_their_certificates](https://wiki.archlinux.org/index.php/Firefox#Firefox_disables_all_extensions_due_to_Mozilla_not_renewing_their_certificates)
EDIT: And I don't have to have studies set to on. :)

---

### Post by DuckHook on 2019-05-04
> **1fallen said:**
> Just to add to your dilemma: Until a fix is out for all, you can temporarily re-enable all extensions by… executing the following code 
… And I don't have to have studies set to on…
Thanks for the above.

I'm not remotely familiar with real coding, but in practical terms, isn't this workaround the same as setting [FONT=Fixedsys]xpinstall.signatures.required[/FONT] to [FONT=Fixedsys]false[/FONT]?

One disables the signature requirement altogether whilst the other fools FF into seeing all extensions as properly signed. Either method bypasses a security measure.

Enabling reporting to Mozilla also bypasses a security measure in my books, but that's a personal measure based on a general dislike of any sort of reporting. It doesn't bypass an *inherent* security measure. 

So, I've just talked myself into enabling studies as the best of a bad situation.

Thanks for helping me think it through. ;-)

---

### Post by #&amp;thj^% on 2019-05-04
> **DuckHook said:**
> Thanks for the above.

I'm not remotely familiar with real coding, but in practical terms, isn't this workaround the same as setting [FONT=Fixedsys]xpinstall.signatures.required[/FONT] to [FONT=Fixedsys]false[/FONT]?

One disables the signature requirement altogether whilst the other fools FF into seeing all extensions as properly signed. Either method bypasses a security measure.

Enabling reporting to Mozilla also bypasses a security measure in my books, but that's a personal measure based on a general dislike of any sort of reporting. It doesn't bypass an *inherent* security measure. 

So, I've just talked myself into enabling studies as the best of a bad situation.

Thanks for helping me think it through. ;-)

You know I thought the same but check my screenshot still set to ask.
Gosh it's sooo hard to stay private with data these days. :( I don't wan't to just because they tell me to, give my data to Mozilla with out fight anyway.:lolflag:

---

### Post by DuckHook on 2019-05-04
> **1fallen said:**
> You know I thought the same but check my screenshot still set to ask.
…yes, but that query is rendered pointless if every extension will automatically pass the check (even if not actually signed). That's my parsing of the arch code at any rate.
> Gosh it's sooo hard to stay private with data these days. :( I don't wan't to just because they tell me to, give my data to Mozilla with out fight anyway.:lolflag:
Very true. As soon as the certificate mess is straightened out, I intend to revert my reporting back to highly restrictive.

---

### Post by wildmanne39 on 2019-05-04
My firefox has fixed itself with the latest update.

---

### Post by VinDSL on 2019-05-04
[**[SIZE=3]Mozilla issues Firefox fix after expired certificate disabled all add-ons[/SIZE]**]("https://venturebeat.com/2019/05/04/mozilla-issues-firefox-fix-after-expired-certificate-disabled-all-add-ons/?utm_source=veooz&utm_medium=referral")
*PAUL SAWERS  @PSAWERS  MAY 4, 2019 8:22 AM*

---

### Post by #&amp;thj^% on 2019-05-04
> **DuckHook said:**
> &#8230;yes, but that query is rendered pointless if every extension will automatically pass the check (even if not actually signed). That's my parsing of the arch code at any rate.

Very true. As soon as the certificate mess is straightened out, I intend to revert my reporting back to highly restrictive.

Same thought again but was told by a credible source that it (The Code) is just a onetime deal (Get out jail free card), the fix looks like its rolling out out now though>> with what I see here in this forum and others.
I'm ok with what I did in the above post, will keep an eye on any thing important to report back, but I expect there will be nothing.
Good to see your MoJo back though, nothing compares to the DuckHook's wisdom in words. (Boom Drops Mike) :KS
see wilmanne39 is already flying high on FF.
@Vin DSL nope not going to that. :p lol>>> I trust Mozilla about as much as I trust Microsoft and Google.

---

### Post by DuckHook on 2019-05-04
> **1fallen said:**
> …I trust Mozilla about as much as I trust Microsoft and Google.

Trying to get blush out of me are ya? :redface:

Actually, I **do** trust Mozilla, else wouldn't be using their browser. I simply don't like reporting—on general principles. It's like brushing one's teeth… just a good habit to cultivate.

---

### Post by #&amp;thj^% on 2019-05-04
> **DuckHook said:**
> Trying to get blush out of me are ya? :redface:


Just reporting it how I see it, your a keeper for sure.
> **DuckHook said:**
> 
Actually, I **do** trust Mozilla, else wouldn't be using their browser. I simply don't like reporting&#8212;on general principles. It's like brushing one's teeth&#8230; just a good habit to cultivate.
You know me better than that (I'm just a rebel LOL) we do agree though on general principles. And deep down I'm with ya.
And this now reported:
>     We rolled out a hotfix that re-enables affected add-ons. The fix will be automatically applied in the background within the next few hours. For more details, please check out the update at [https://support.mozilla.org/en-US/kb...nstall-firefox](https://support.mozilla.org/en-US/kb...nstall-firefox)
    We are working on a general fix **_that doesn&#8217;t use the Studies system_** and will keep this blog post updated accordingly.

    We will share a more substantial update in the coming days.
    [https://support.mozilla.org/en-US/kb...nstall-firefox](https://support.mozilla.org/en-US/kb...nstall-firefox) 



---

### Post by scriber on 2019-05-05
I'm still waiting for the fix to happen, kinda annoying with my password manager ( and other things ) not working.

Have temporarily switched to Opera ( which I use for online banking ) 

The fix was applied in my Win 10 and Linux Mint installs but not Ubuntu 18.04.2

---

### Post by donbcilly on 2019-05-05
Funny, on my Kubuntu 18.04.2 it fixed itself (no action on my part) within one-two hours. 66.0.3 (64-bit)

Still... Opera is getting better, isn't it?
I currently have it as my Facebook-only browser - I usually have a designated browser for it, only use it for that, and don't use it on the others, as it reduces the level of annoyance both ways - but I'm thinking of designating something else (I don't really use FB anymore anyway) and starting to use it for more things :)

---

### Post by Holger_Gehrke on 2019-05-05
@scriber: if the update still hasn't happened, try entering 'about:studies' into the address bar. The studies that contains the hotfix both have the number of the bug (1548973) in their name. One of the studies updates the certificate, the other sets the date of certificate update. There's a link at the top of that page to the item in about:preferences you have to set to allow studies. Update the 'about:studies' page after allowing studies if they weren't enabled before. For me the fix came in within half an hour after allowing studies. I've set this back to not allow studies or report any data to Mozilla and have not had any problems since.

Holger

---

### Post by scriber on 2019-05-05
> **Holger_Gehrke said:**
> @scriber: if the update still hasn't happened, try entering 'about:studies' into the address bar. The studies that contains the hotfix both have the number of the bug (1548973) in their name. One of the studies updates the certificate, the other sets the date of certificate update. There's a link at the top of that page to the item in about:preferences you have to set to allow studies. Update the 'about:studies' page after allowing studies if they weren't enabled before. For me the fix came in within half an hour after allowing studies. I've set this back to not allow studies or report any data to Mozilla and have not had any problems since.

Holger

I did all that yesterday, and it shows the 2 items as Active but still nothing.

---

### Post by kesetyan on 2019-05-06
I'm still waiting for the fix for Firefox in my Lubuntu 18.04 system.  This dual boots with Windows 7 in which Firefox automatically updated from v 66.0.3 to v 66.0.4 earlier today but no such luck in Lubuntu.  As I posted in the 'Firefox add-ons disabled and fail to download' thread in the 'Ubuntu, Linux and OS Chat' section, I have now installed and set up the Vivaldi browser which is doing all I require with bookmarks copied from Firefox and all the add-ons I had in Firefox compatible with Vivaldi.  If Firefox doesn't automatically fix soon, I may ditch it.

---

### Post by scriber on 2019-05-06
> **kesetyan said:**
> I'm still waiting for the fix for Firefox in my Lubuntu 18.04 system.  This dual boots with Windows 7 in which Firefox automatically updated from v 66.0.3 to v 66.0.4 earlier today but no such luck in Lubuntu.  As I posted in the 'Firefox add-ons disabled and fail to download' thread in the 'Ubuntu, Linux and OS Chat' section, I have now installed and set up the Vivaldi browser which is doing all I require with bookmarks copied from Firefox and all the add-ons I had in Firefox compatible with Vivaldi.  If Firefox doesn't automatically fix soon, I may ditch it.

Same situation with me and Ubuntu 18.04.2

Win 10 and Mint both updated but not Ubuntu.

Had to switch to Opera for now and use Win 10 for main use.

---

### Post by kesetyan on 2019-05-08
Today (Wednesday 08 May 2019) at about 14:00 British Standard Time, Software Updater notified me that there was a Firefox update available.  I updated the program and now all is well with Firefox - all my previous settings remained and all my add-ons are working as normal.  I hope all others, who had similar problems with Firefox, will find the issue is resolved for them as well.

Cheers.

---

### Post by scriber on 2019-05-08
> **kesetyan said:**
> Today (Wednesday 08 May 2019) at about 14:00 British Standard Time, Software Updater notified me that there was a Firefox update available.  I updated the program and now all is well with Firefox - all my previous settings remained and all my add-ons are working as normal.  I hope all others, who had similar problems with Firefox, will find the issue is resolved for them as well.

Cheers.

Same here, wonder why it took so long for some systems ?

---

