---
title: "Icon size in Dash"
date: 2015-06-13
forum: General Help
---

### Post by ChezStan on 2015-06-13
Hi,

I use the Compass icon set in Ubuntu 15.04. Those icons are svg only.

In order to associate proper icons to the apps for which Compass does not have any, I heavily rely on the ~/.local/share/applications .desktop files.
The only glitch is that these icons appear far bigger in the dash than the ones automatically assigned by the icon set. Check this picture : Calibre, e-book-viewer, Dpluzz, Qarte & Tor.

[IMG]http://ismayotte.lautre.net/www/07.png[/IMG]

My question is : Do I have to create different icons ? Maybe png's ? In the affirmative, what size, and where should I place them ?

Thanks for any hint you could provide me with.

Stan.

---

### Post by mc4man on 2015-06-13
It could be that .png's that aren't in a standard location can get miss-sized in the Dash.
What is the size of the 'normal' icons you show that are using .png?, looks like either 48x48 or 64x64 px in screen but hard to really tell.
Where is the location of one of the oversized .png's if it is appearing in the Dash bigger than it's actual size?

---

### Post by ChezStan on 2015-06-13
They are all in the /usr/share/icons/Compass/apps/48 folder (the only one containing all the apps icons)! some I edited (such as Qarte) and some just being linked to from the .desktop file. Even when edited, I kept the original svg size... There is no png at all for the time being !
For example, the e-book-viewer icon only uses the regular cairo-dock.svg icon.

Here is its .desktop file
[IMG]http://ismayotte.lautre.net/www/screenshot16.png[/IMG]

---

### Post by ChezStan on 2015-06-13
Would it be ill-advised to file a bug report for such a minor issue ?

---

### Post by ChezStan on 2015-06-14
Little up... 

No one really ?  :confused:

And what about my question on filing a bug report ?

---

### Post by ChezStan on 2015-06-14
I finally found the answer.

As you can see in the above screenshot, I filled the icon entry of my .desktop file with the absolute path to the icon. Dash, one way or another did not re-calcultate the size of the icon.

Instead, I just entered the name of the icon. (Of course, one gets to create the icon in every and single iconset one wants to use.)

[IMG]http://ismayotte.lautre.net/www/09.png[/IMG]
And then, the dash finally acts with the icon as it does for any other "normal" application.

Better looking, isn't it ?

[IMG]http://ismayotte.lautre.net/www/08.png[/IMG]

---

