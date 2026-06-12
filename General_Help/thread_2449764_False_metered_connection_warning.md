---
title: "False metered connection warning"
date: 2020-09-02
forum: General Help
---

### Post by nought2 on 2020-09-02
I'm trying out 20.04.1 Focal.
Gnome Tweaks has been installed. The Dash to Dock extension has been added to Tweaks.

Initially Dash to Dock was working normally. 
A few days after installing it began to play up. When trying to access its functions in the dock sometimes I would get the standard dock behaviour and at others I'd get Dash to Dock behaviour. Sometimes when showing or hiding the dock with mouse cursor movement two dock panels superimposed on each other would slide into or out of view.

I checked the Tweaks screen to see what was going on. It showed the sliding switch beside Dash to Dock was set to deactivated. But Dash to Dock is still working albeit inconsistently. Beside the Dash to Dock settings icon was a ! warning triangle:
[ATTACH=CONFIG]286860[/ATTACH]

Clicking on the warning or notification triangle opened a Software window:
[ATTACH=CONFIG]286861[/ATTACH]

Clicking the Find Out More tile caused an Automatic Updates Paused notification to appear. It says automatic updates have been paused because the computer is using a metered connection.
That is half right. 
I use my phone's mobile wifi hotspot for my internet connection. While strictly it is a metered connection I am not using it that way for my Ubuntu OS installations.
In Settings > WiFi connection manager > [hotspot_name] the box beside "Metered connection: has data limits or can incur charges" is unchecked.

I have one other Tweaks extension installed and it is not affected. Maybe its developer has not pushed an update out to users recently and Dash to Dock has.

I have witnessed this change twice. When OS was new and fresh and D2D just installed, D2D worked normally. The false metered connection problem manifested a day or two after installing D2D. A few days later I wound the system back to an earlier image. D2D was working normally again. After an hour or so connected to the internet the problem manifested again. I am guessing that the image was made before D2D update was pushed out.

Is there any way I can allow automatic updates of Tweaks extensions to proceed?
Could it be a bug? With 20.04.1 Focal or with Dash to Dock?

---

### Post by gtisza on 2021-03-20
See [https://gitlab.gnome.org/GNOME/gnome-software/-/issues/996](https://gitlab.gnome.org/GNOME/gnome-software/-/issues/996)

---

