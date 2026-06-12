---
title: "Firefox - Arrows disappeared from scrollbar"
date: 2016-05-19
forum: General Help
---

### Post by Mel_Blakey on 2016-05-19
Since upgrade to Firefox 46 I no longer have the 'up' 'down' arrows on the scrollbar.

I have had a good look around and there is a mention of a change to gtk-3.0 by Firefox.

I am a relative novice and havn't got a clue what this means.

Can someone please explain how to get my arrows back or advise on how to revert back to FF45

Thanks

---

### Post by vasa1 on 2016-05-19
It's not really a good idea to drop back a version for something like that!

You can still scroll up or down with the up and down arrows of your keyboard or page up or down!

Anyway, you could try editing the *gtk-widgets.css* file of your gtk3 theme to change```
    -GtkScrollbar-has-backward-stepper: false;
    -GtkScrollbar-has-forward-stepper: false;
```to```
    -GtkScrollbar-has-backward-stepper: true;
    -GtkScrollbar-has-forward-stepper: true;
```This, of course, assumes that your theme supports arrows in scrollbars.

On an unrelated note, you may also want to edit ~/.config/gtk3/settings.ini to include```
gtk-primary-button-warps-slider=false
```to enable legacy scrolling.

---

### Post by Mel_Blakey on 2016-05-20
Hi
Thanks for the reply. (sorry for the delay in responding)

I have previously enabled legacy scrolling.

The problem that I have is that can't find *the gtk-widgets.css* file

---

### Post by jim_deadlock on 2016-05-20
I always use the mouse wheel for scrolling, I think that's what most people do and maybe the reason for removing the arrows.

---

### Post by vasa1 on 2016-05-20
> **Mel_Blakey said:**
> Hi
Thanks for the reply. (sorry for the delay in responding)

I have previously enabled legacy scrolling.

The problem that I have is that can't find *the gtk-widgets.css* file

Could you mention which theme you're using and where it's located? Is it in */usr/share/themes* or *~/.themes* or *~/.local/themes*?

---

### Post by Mel_Blakey on 2016-05-20
As I say, I am a linux novice. But, have used Ubuntu 14.04 as it came (out of the box) for 2 years. Its been fantastic but I am not sure what theme it uses. :(

---

### Post by vasa1 on 2016-05-20
> **Mel_Blakey said:**
> As I say, I am a linux novice. But, have used Ubuntu 14.04 as it came (out of the box) for 2 years. Its been fantastic but I am not sure what theme it uses. :(
In that case, you'll have to wait until a Ubuntu 14.04 user comes along.

If you have _never_ changed themes, it's possible you're using **Ambiance** and that's in */usr/share/themes*. The file that needs to be modified would then be */usr/share/themes/Ambiance/gtk-3.0/gtk-widgets.css*. To modify that file, you'll need elevated privileges. 

The relevant section seems to be:```
/*************
 * scrollbar *
 *************/
.scrollbar {
    -GtkScrollbar-has-backward-stepper: 0;
    -GtkScrollbar-has-forward-stepper: 0;
    -GtkScrollbar-trough-border: 0;
    -GtkScrollbar-min-slider-length: 31;
    -GtkRange-slider-width: 10;

    background-color: @scrollbar_track_color;
    background-image: none;
    background-size: 0;
    border: none;
    border-radius: 0;
}

```in which you'll need to change 0 to 1 for the backward and forward steppers.

If you are unsure, I suggest you leave things as they are and just live without the arrows. They really aren't necessary. Several themes have dropped them. I've never used them, even when they were there.

---

### Post by Mel_Blakey on 2016-05-20
Hi
Thanks for your input.

I do appreciate your opinion. But, I use my laptop out in the field, in a vehicle where it is awkward to use a mouse. So, the up / down arrows are essential to me and quite a few others who are also asking the question. Also, the up / down keys do not work on all websites.

Can you advise the best way to roll back to FF45?

Regards

---

### Post by jim_deadlock on 2016-05-20
Laptop touchpads usually have a finger action for scrolling. Try 2-finger drag or 1-finger on the right side of the pad. Just a thought.

---

### Post by Mel_Blakey on 2016-05-20
Marvellous Jim..... That works a treat, better than the Scroll Buttons.

Thanks :D

---

### Post by x-contact-u on 2016-06-18
Thanks for the advice - that's fixed it for me too!  :)

---

