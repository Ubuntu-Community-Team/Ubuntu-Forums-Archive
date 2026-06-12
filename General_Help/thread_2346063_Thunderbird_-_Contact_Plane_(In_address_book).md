---
title: "Thunderbird - Contact Plane (In address book)"
date: 2016-12-10
forum: General Help
---

### Post by poisonfor3 on 2016-12-10
I did search and search and I seem to be the only person with this problem. 

PROBLEM:
When you open the address book on the left is the "directory plane" that works fine. On top you have your contacts and on the bottom (If you choose to have it displayed) is the Contact Plane. You can make it show up or make it go away by using your setting. Thing is . . . when I have it being displayed it is completely blank. It should show the information of the contact you have selected. At first I did not give it much thought because I was not using it much but now I need to.

INFO
Release 16.04.1 LTS (Xenial Xerus) 64-bit
Kernel Linux 4.4.0-47-generic x86_64
MATE 1.12.1
Tbird - 45.4.0

HISTORY
It worked fine when I was using windows. I had the portable version and used wine when I was on a Linux system. All was good. I made the choice to just not use windows (unless there is a program or job that I must) at all for my day to day use. AND get rid of the need to use Wine. I did that. All is good. Much happier with native linux programs. Just working out some bugs like this.

Like I said I have looked and looked and no one seems to have this problem. All the contacts are right where they should be and work just fine. Just can not see them in the contact plane. I first tried disabling all the addons. Same thing. I have search this site and the internet, I tried finding addons to use as a work around. No such luck. Not s programer but I know Thunderbird very very well. To give old timers an idea how long I have been using it I switched over to T-bird from Pegasus Mail and used nerdshack for my pop. Back then google's gMail had a cap on how much email you could store with them. So please now that the setting withing T-bird are set right albeit there may be a problem with the about:config. I have snooped around there but all looks good from what I can tell. 

Anyone have ideas as to why I can not see my contacts in the Contact Plane?

Thanks for at least reading about my problem.  :popcorn:
-Annie

---

### Post by howefield on 2016-12-11
First thing I would suggest is to update your installation.

There are updates to both Thunderbird and the kernel versus the versions that you posted. Likely as not it won't automagically fix the problem but may as well tackle it from an up to date system.

---

### Post by poisonfor3 on 2016-12-11
I have not found the reason why. I have found something new and what looks to be a work around albeit not a good one. It is not all of the contacts that are doing it. Only some are doing it. Others contacts in other address books seem to work fine. When I move a contact from a address book that has contacts in it that ARE WORKING, to a address book that has contacts in it that are NOT working, the contact still shows up in the contact plane. So the contacts that are working stay working no matter where I move them. So it is a problem with the contacts not the address books. ALSO new contacts work just fine. So looks like I could make new contacts for the 5.000 contacts that are not working, move all the information from the bad contact to the good (new) contact by hand. 20 years later I will be all done. I may be able to bulk export them and bulk import them into new contacts but not sure if that will work and will be filled with bugs just because things like that always are :) So that may me my work around; better if I can just fix them all at once because what if I do that and the problem comes back?



That is not strange here is where it gets strange:
When you move a contact THAT IS NOT WORKING from an address book where none of the contacts are working, to a address book where THEY ALL ARE WORKING it will work, kinda. It will only work if you FIRST click onto a contact that is working. In fact I can get all the contacts working IN THE BROKEN ADDRESS BOOKS when I FIRST click on "A GOOD (OR NEW) CONTACT". So I can get them working that way. Yet I will end up with a mix of contacts some work right when others don't. Oh but wait it gets stranger. If i right click onto a contact that is NOT working and "edit as new" to make a clone of it. The new clone is broken too, plus the photo will not work with the new contact. In other words to get a contact working you have to make a brand new contact and transfer all the information by hand; a clone of the same one will not work. So it is something in the contact that is clone-able that is braking them. Whole address books are broken or not broken but the contacts can be moved to and from broken address books and stay broken or not broken what ever the state that they where in. So the contacts are broken not the address books but the address books are tied into the way (somehow) that the contacts got broken in the first place. I told you it was strange.

So this may have happened to just me. As I went from windows portable to Linux seems to be where the problem started; there may have been something to do with that.

Yea, I was going to do same backups and updates. Updates I know are needed but I have has so many things brake over the years after an update, they now scare me. In fact they have always seem to brake more things than they fixed. BUT that comes from years of working with windows back when XP was new so what you expect. IN FACT it was windows 10 update that "pushed me over the edge". I tried to hang on but Microsoft just kept kicking me in the face until I went to Linux. :)

LOL for the people that may think I am just paranoid. Here is an update for T-Bird dated Nov. 18 2016:

[h=4][CVE-2016-5294: Arbitrary target directory for result files of update process]("https://www.mozilla.org/en-US/security/advisories/mfsa2016-93/#CVE-2016-5294")[/h]   ReporterHolger FuhrmannekImpacthigh   [h=5]Description[/h]   The Mozilla Updater can be made to choose an arbitrary target  working directory for output files resulting from the update process.  This vulnerability requires local system access. 
*Note: this issue only affects Windows operating systems.*
        [h=5]References[/h]     
[LIST]
[*][Bug 1246972]("https://bugzilla.mozilla.org/show_bug.cgi?id=1246972")
[/LIST]


Good to have fixed for them Widows people. Does not fix my problem. :(

Update: seems like it may in fact be one of the addons. I tried safe mode again and this time it worked like it should. I will install them one at a time or un-install them one at a time and see if I can get it fixed.

---

### Post by poisonfor3 on 2016-12-11
It was the AddressBookTab addon the whole time. 

Strange because  the very first thing I tried was to start-up thunderbird in safe mode  and test it. Seems like I may not have did a good test. After I went to  the mozilla addons website:

[https://addons.mozilla.org/en-US/thunderbird/addon/addressbooktab/?src=search](https://addons.mozilla.org/en-US/thunderbird/addon/addressbooktab/?src=search)

It  clearly states that it is only good for v3.0 to v28.0 and there are a  bunch of reviews on how after v45 it "now causes Contacts to be buggy"  with people like me crying to see it go.

@[[COLOR=#990303]**howefield**[/COLOR]]("https://ubuntuforums.org/member.php?u=186490")  It was because I was updating my thunderbird that caused the problem.  If I stuck with v45 my addon would still be working. My system may have  crashed with crypto/spy/bugs but my address book would have worked the  way I wanted . . . for a little bit. :lolflag:


Maybe  someone with the same problem will google and find this post and  disable the addon before wasting as much time on it as me.

Thanks howefield and to all that did read this to try to help.
-annie

---

