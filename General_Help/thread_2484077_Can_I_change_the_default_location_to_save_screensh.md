---
title: "Can I change the default location to save screenshots?"
date: 2023-02-16
forum: General Help
---

### Post by sofasurfer on 2023-02-16
Can I change the default location to save screenshots? I downloaded dconf editor but that seems to not have an option got that. Any ideas?

---

### Post by ne29914 on 2023-02-17
Depends on how you take screenshots. You provide 0 information.

---

### Post by dragonfly41 on 2023-02-17
I use Flameshot which provides various options for saving.

---

### Post by deadflowr on 2023-02-17
We assume the default Ubuntu installation unless otherwise told so.

More important is what version of Ubuntu since they change the way things work all the time.

[s]For Ubuntu 22.04 in dconf editor  you should be able to set/change the default auto save location in org > gnome > gnome-screenshot > auto-save-directory.
You need to toggle default value setting off and then add your new location in the custom value field. Then click on the Apply button in the bottom right when it shows.


For other versions of Ubuntu, I don't know..[/s]

Edit: Nevermind, I realized I also have unity installed so it includes gnome-screenshot, which Ubuntu proper does not.

So, yeah, don't know.
Sorry being wasteful.

---

### Post by mIk3_08 on 2023-02-18
> **sofasurfer said:**
> Can I change the default location to save screenshots? I downloaded dconf editor but that seems to not have an option got that. Any ideas?
I haven't tested it yet but I think you can easily change the default location value of your screenshot directory using dconf configuration. 
My dconf in Ubuntu 22.04 LTS see image below. Regards and cheers.

---

### Post by deadflowr on 2023-02-18
> **mIk3_08 said:**
> I haven't tested it yet but I think you can easily change the default location value of your screenshot directory using dconf configuration. 
My dconf in Ubuntu 22.04 LTS see image below. Regards and cheers.

Wrong screenshot utility.
That deals only with the totem video player screenshots and has nothing to do with the gnome shell desktop's screenshot utility.

Found a bug report on this issue here: [https://gitlab.gnome.org/GNOME/gnome-shell/-/issues/5454]("https://gitlab.gnome.org/GNOME/gnome-shell/-/issues/5454")
(Which I find funny because they keep closing duplicates even though the duplicates have more, better, or seemingly actual  answers, than the report that's been kept open.)

What's weird to me is that screenshots are both saved to the Pictures/Screenshots directory and to the clipboard.
So you can paste the image from the clipboard into whatever directory you want, but it's also already saved to the default location.

I guess if the required behavior is to always ask where to save r set a location you want instead of using whatever location gnome shell sets it as, then the solution might as well try a different screenshot program such as flameshot or gnome-screenshot. Or even something else entirely.
I think if you want to use either of those with the keyboard shortcuts you'll probably need to go into setting and reset those so they don't use the system's screenshot tools and use the ones for the program you decided to use instead.

---

