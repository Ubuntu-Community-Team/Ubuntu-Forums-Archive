---
title: "GRUB2 theme edit scrren text"
date: 2024-05-14
forum: General Help
---

### Post by rolfbruge on 2024-05-14
This is a reattempt to post this question as it did not appear the first post attempt concluded.

This is a rather specific question regarding how to configure GRUB2 in order to specify the text color for an on-the-fly edit.

When highlighting a selection from the GRUB2 menu one of the available choices on screen is to press "e" to view the underlying menuentry configuration.

Would like to specify the menuentry cofiguration text color in the "edit" screen to cortrast with the theme background.

Alternatively,, to specify the menuentry cofiguration background (not the desktop-image) color in the "edit" screen to contrast with the text color.

theme.txt has these parameters, and changing each one does not affect the "edit" text color:

# general settings
title-color: "whatever"
message-color: "whatever"
message-bg-color: "whatever"
desktop-image: "background.png"
desktop-color: "whatever"

Is there a specific parameter syntax within theme.txt, under "general settings" or elsewhere, that regulates the "edit:" function text color?

---

### Post by tea for one on 2024-05-14
No, I'm sure that you cannot edit the appearance of Grub "on-the-fly"
Permanent alterations need to be made after the OS has booted.

[https://github.com/hartwork/grub2-theme-preview](https://github.com/hartwork/grub2-theme-preview)
Perhaps this link is useful?
Not a recommendation, just offering info.

---

### Post by rolfbruge on 2024-05-14
Tea for One.

Think you misunderstood on-the-fly editing.

This was a reference to how to change the grub2 menuentry configuration, then press F10 to boot.

The question was how to specify the edit windows text color, with the intent to reboot in order to see a different color text in the edit screen.

What parameter controls the edit screen text color and where to configure that parameter.

---

### Post by dragonfly41 on 2024-05-14
I do not know how to change existing default grub theme. But I do know that if you install rEFInd (which supplements GRUB and sits alongside in EFI) you can customise rEFInd GUI theme quite easily.

---

### Post by tea for one on 2024-05-14
> **rolfbruge said:**
> Tea for One.
Think you misunderstood on-the-fly editing.
This was a reference to how to change the grub2 menuentry configuration, then press F10 to boot.
The question was how to specify the edit windows text color, with the intent to reboot in order to see a different color text in the edit screen.
What parameter controls the edit screen text color and where to configure that parameter.
To change the colour of the Grub text, you have to edit [COLOR="#0000FF"]/etc/grub.d/05_debian_theme[/COLOR]
You edit this after you have booted the operating system and the appearance of Grub will be different during the next boot.
Here are the instructions [https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)

---

### Post by rolfbruge on 2024-05-15
Thank you Tea for One

In addition to commenting out some potentially conflicting configuratiion information, the solution was to edit the /etc/grub.d/05_debian_theme portion of the GRUB2 configuration file and add parameter: 

set color_normal=x/y

where "x" is the specified text color of the edit window and "y" is the specified background color of the edit window.

Thank you again for your help.

---

### Post by tea for one on 2024-05-15
Pleased to have helped.
It's a nice gesture to mark the thread as solved - very helpful for other forum members/searchers:-
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

