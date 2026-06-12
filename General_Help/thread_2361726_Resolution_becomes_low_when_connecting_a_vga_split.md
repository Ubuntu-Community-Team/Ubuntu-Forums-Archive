---
title: "Resolution becomes low when connecting a vga splitter"
date: 2017-05-20
forum: General Help
---

### Post by offir on 2017-05-20
i have ubuntu 16.04 
i try to connect to the Graphic card [COLOR="#800080"](GeForce GTX 650)[/COLOR] two screen
[COLOR="#0000FF"]SAMSUNG syncmaster b1940[/COLOR]
and
[COLOR="#FF0000"]LG flatron L1954sm[/COLOR]
When each screen is connected alone
The maximum resolution is 1280x1024 wich is what I want

For a reason I could not find
If I connect the two screens to the computer at the same time
One of them does not work (it will always be the second screen I connect)

my Graphic card has two dvi connectors
I plug a [COLOR="#FF0000"]DVI to VGA adapter[/COLOR] into a graphics card
The screens are connected using a vga cable
I need to show the same picture on both screens
So I tried to connect the screens to the [COLOR="#FF0000"]VGA splitter[/COLOR]
I tried the [COLOR="#0000FF"]splitter VS-814[/COLOR] [http://www.tfl.co.il/Uploaded/VS-812H.pdf]("http://www.tfl.co.il/Uploaded/VS-812H.pdf")
The maximum resolution was 1024x768
So I tried the [COLOR="#FF0000"]simpler splitter as in the picture[/COLOR]
The maximum resolution is 1152x864
In the meantime I am with the simple splitter
I want to understand why it is impossible to put a higher resolution


i try to use xrandr to adjust to high resolution
But there is no possibility
I get an error message Maybe because of the splitter

Is this possible at all ??

---

### Post by gordintoronto on 2017-05-20
With a DVI adapter, the video drivers expect to get input about the monitor. Adapters often block this information.

I suggest two DVI cables, then I think you can tell Nvidia X Server Settings to display the same picture on both screens. However, it might not be possible, since they have different resolution.

---

