---
title: "Unread Mail Indicator?"
date: 2020-01-25
forum: General Help
---

### Post by 2CV67 on 2020-01-25
Hi!

For many years, first with FireTray add-on, then without, I have enjoyed having a clear indicator of the number of unread messages displayed on the Thunderbird Tile.

Recently (I think with the upgrade from 19.04 to 19.10?) that indicator seems to have disappeared.

Today I am using "Dash to Panel" Gnome Extension which gives me lots of nice options, but no unread message indicator.

I also have Gnome Tweaks, but again without any unread message indicator, as far as I can see.

I have just found & installed Gnome Extension "New Mail Indicator" which does a similar job.
It does not show the number of unread mails, but does indicate that at least one new mail has arrived since the last visit to TB.
That does eliminate the need to keep visiting TB to see if there are new mails (an unbelievable chore!!!) so I am thankful for that!

Is there any better solution?

If not, is there any way I can have a more obvious indicator sign for NMI?
Currently, a drab black envelope is replaced by a drab black round thing which is hardly eye-catching!

Is this regression considered a bug?
I think it should be. (So maybe I know what to do next...)

Thanks for any other suggestions!

---

### Post by walts48 on 2020-01-25
Thunderbird uses native Linux notifications since version 60.

[https://www.thunderbird.net/en-US/thunderbird/60.0/releasenotes/](https://www.thunderbird.net/en-US/thunderbird/60.0/releasenotes/)

I'm using Ubuntu 18.04.3 LTS and when I have "Show an alert" enabled in Preferences > General I get a notification. Right now it is disabled so all I hear is the default sound when new mail arrives.

I prefer the old non-native Linux notification which can be enabled by going to Preferences > Advanced, click the Config Editor button, search for the word "biff", and change "mail.biff.use_system_alert" to false. Those are the notifications I see when I have "Show Alerts" enabled.

[URL="https://www.thunderbird.net/en-US/thunderbird/60.0/releasenotes/"]


[/URL]

---

### Post by 2CV67 on 2020-01-31
I am finding the New Mail Indicator Gnome Extension very useful & nearly good.

Is there any way I can have a more obvious indicator sign for New Mail?
Currently, a drab black envelope is replaced by a drab black round thing which is hardly eye-catching!
If the drab black envelope changed to a bright yellow or blue envelope with New Mail, that would be much better for me.
I didn't find any way to contact the developer (fthx) to ask this question.

---

### Post by fthx on 2020-02-03
Strange.
The unread email icon is this one :
/usr/share/icons/Adwaita/scalable/actions/mail-mark-important-symbolic.svg
It should exist in any GNOME install ?

It looks like the red envelope here :
[https://extensions.gnome.org/extension/1505/new-mail-indicator/](https://extensions.gnome.org/extension/1505/new-mail-indicator/)
The red color is eye-catching since all GNOME panel is black/white (unless Dash to Panel is installed...). I will not change this since I find it ok.

Anyway, if it isn't working for you, you can edit the extension.js you can find in ~/.local/share/gnome-shell/extensions/new-mail-indicator@fthx.
The new icon name is to be included here :
```
if (count > 0) {
            mail_icon = '**mail-mark-important-symbolic**';
        } else {
            mail_icon = 'mail-unread-symbolic';
        };
```

Please note that I removed the unread mails counter since the way this extension works (just detect the Thunderbird GNOME notifications) does not make it reliable (e.g. 2 emails incoming, 1 notification). IMHO, it's not important to know that I've 2 or 7 unread emails, just that I have to show TB windows to check new emails. Additionally, note that you can open/show the TB window by clicking on the envelope.

---

### Post by fthx on 2020-02-03
Ok I think you use Yaru icon theme ?
Could you please try to put :
**/usr/share/icons/Adwaita/scalable/actions/mail-mark-important-symbolic.svg**
instead of :
**mail-mark-important-symbolic**
(and same action for the other icon ?).

---

### Post by 2CV67 on 2020-02-04
Thanks very much fthx for your interest & help!

I agree the number of unread mails is not very useful.

I confirm I am using Yaru icons and also Dash-to-Panel extension.

I tried (with Tweaks) switching all icons to Adwaita & succeeded in getting your intended icons to display.
But I generally prefer Yaru, so switched back to Yaru.

I tried (in extension.js) replacing
**mail-mark-important-symbolic**
by
**/usr/share/icons/Adwaita/scalable/actions/mail-mark-important-symbolic.svg**
but with no immediate effect.
I found I needed to re-login to see any change.
Then the change was not as expected.
When new mail arrived, the black envelope icon disappeared but no new icon appeared.

Going back to your previous post, I looked for a suitable icon in Yaru/scalables & found a good bright yellow one:
/usr/share/icons/Yaru/scalable/status/software-update-urgent-symbolic.svg
so I replaced
**mail-mark-important-symbolic**
by
**software-update-urgent-symbolic**
and that works OK.

Actually, it's slightly less than OK as the new icon on my dock/panel is a dull orange instead of a bright yellow, but it will do for me.

Thanks again for your help!

---

### Post by 2CV67 on 2020-02-05
Happy enough now with New Mail Indicator Gnome Extension, but still curious to see if I can get a more obvious indicator. 

I made a new Yellow-Envelope scalable icon in LibO Draw & saved it with my other (now old) icons at:
/home/chris/Pictures/Icons/newmail.svg

fthx said:
> Anyway, if it isn't working for you, you can edit the extension.js you can find in ~/.local/share/gnome-shell/extensions/new-mail-indicator@fthx.
The new icon name is to be included here :
```

if (count > 0) {
            mail_icon = '**mail-mark-important-symbolic**';
        } else {
            mail_icon = 'mail-unread-symbolic';
        };
```

I tried a few combinations but nothing seemed to work.
How exactly can I introduce my new icon there?

Thanks again & I repeat this is a luxury, not a necessity!

---

### Post by fthx on 2020-02-07
I worked at a local icon feature some days ago but with no success. You have to add your local image folder to the active theme's icons folder path. It's not trivial.
I suggest you simply add your image to /use/share/icons/Yaru/scalable .

I've just uploaded a new version with standard read/unread icons to avoid the bizarre (!) icon in Yaru. But it does not match your needs.

---

### Post by 2CV67 on 2020-02-07
OK & thanks again for your efforts!

Please don't waste any more of your time on this one.

---

### Post by 2CV67 on 2020-02-07
> **fthx said:**
> I suggest you simply add your image to /use/share/icons/Yaru/scalable .

Just for completion, in case anybody else is following this...

I did add my image to Yaru/scalable/actions.
I needed to do that as Administrator, which I try to avoid.
It didn't work first time (result = no icon when new mail).
I blindly tried changing the name from newmail.svg to newmail-symbolic.svg & then it worked.

But my bright yellow envelope showed as white on the dock/dash/panel!
Where the yellow 'software-update-urgent-symbolic' icon shows dull orange there.
Beats me.

I settled for the orange 'software-update-urgent-symbolic' as the best compromise so far...

---

### Post by fthx on 2020-02-13
Ok, in version 14 (at the moment here : [https://extensions.gnome.org/review/13958](https://extensions.gnome.org/review/13958) ) I make the new mail envelope orange (the Ubuntu's orange).
Tested with Yaru, it seems eye catching.

---

### Post by 2CV67 on 2020-02-14
fthx - I am extremely impressed by your dedication to this topic!
I never saw such rapid reaction to a forum query.
Thank you!

I tried your version 13 but found the yes/no icons still too similar.

I tried your version 14 and found an improvement, but not that much.
The black envelope stays the same - it's just the background which changes from white to orange.
That background is about 1 pixel on my dash which is only 30px total size.

To illustrate my situation, I attach a number of screenshots of the local area of my dash.

Original no-mail/yes-mail icons with Yaru:
[ATTACH=CONFIG]285017[/ATTACH] [ATTACH=CONFIG]285018[/ATTACH]

Version 13 no/yes icons:
[ATTACH=CONFIG]285019[/ATTACH] [ATTACH=CONFIG]285020[/ATTACH]

Version 14 no/yes icons:
[ATTACH=CONFIG]285019[/ATTACH] [ATTACH=CONFIG]285022[/ATTACH]

Continued in next post due to image-per-post limit...

---

### Post by 2CV67 on 2020-02-14
Continued from previous post:

Using Yaru 'software-update-urgent-symbolic' icon (why is it orange when it should be yellow?):
[ATTACH=CONFIG]285023[/ATTACH]

Using my own 'newmail-symbolic' icon but with orange color from version 14:
[ATTACH=CONFIG]285025[/ATTACH]

Using my own 'newmail-symbolic' icon but with bright yellow #FFFF00 color:
[ATTACH=CONFIG]285024[/ATTACH]

In terms of results, I much prefer my icon in yellow to any of the other results.
But it seems to need me to infiltrate my own icon into the Yaru icons folder, which is messy & undesirable.

I tried to change the 'software-update-urgent-symbolic' to #FFFF00 yellow but it stayed orange...

I would like to find a way of changing the version 14 'mail-unread-symbolic' icon from black-on-orange to yellow-on-black, but my blind attempts didn't succeed (yet).

---

