---
title: "Logitech G15 Keyboard Volume Control"
date: 2007-12-28
forum: General Help
---

### Post by Ubiquitous1980 on 2007-12-28
Some users of the G15 Logitech Keyboard may have noticed that the volume control does not work.  This is due to an incorrect keyboard binding in the file:

etc/X11/xkb/symbols/inet

The line that is incorrect is:

key <I2D> { [ XF86AudioRaiseVolume ] };

The I2D needs to be changed to I30

**Restart the X-server by logging out then in** (don't do ctrl-alt-backspace as this is for emergencies)

This solution works for Kubuntu 7.10

---

### Post by Kementari on 2008-01-03
Is there be a G15 section that "<I2D>" would be under? I see a few Logitech keyboards in the lis, but only one has a <I2D> key--and switching it to <I30> had no effect.

---

### Post by Ubiquitous1980 on 2008-01-04
This is strange because my system just reverted and caused the same problems, let me check back with you within a day or two.

Damien

---

### Post by Ubiquitous1980 on 2008-01-04
Hey, Back again with a fix.

I do a blanket change to all logitech keyboards, I know this isn't precise, but i had it revert for some reason.  I changed the reversion back to I30, but this didn't solve it after a log out and log in.  What solved it then was a full reboot.

I hope that helps.

Damien

---

### Post by Kementari on 2008-01-05
Allright, this is what I have under the Logitech section of /etc/X11/xkb/symbols/inet. I'm not exactly sure what you mean by a blanket change, do you mean just adding the line under every section? Should I have an entry for my G15 somewhere in this file? Thanks again. :)
```
// Logitech

// Logitech common definitions
partial hidden alphanumeric_keys
xkb_symbols "logitech_base" {

    key <I01> {	[ XF86AudioMedia ] };
    key <I02> { [ XF86WWW ] };
    key <I10> { [ XF86AudioPrev ] };
    key <I15> { [ XF86Community ] };
    key <I16> { [ XF86ScrollClick ] };
    key <I19> { [ XF86AudioNext ] };
    key <I20> { [ XF86AudioMute ] };
    key <I21> {	[ XF86VendorHome ] };
    key <I22> { [ XF86AudioPlay, XF86AudioPause ] };
    key <I24> { [ XF86AudioStop ] };
    key <I2E> { [ XF86AudioLowerVolume ] };
    key <I30> { [ XF86AudioRaiseVolume ] };
    key <I32> { [ XF86HomePage ] };
    key <I3B> { [ XF86New ] };
    key <I3C> { [ XF86Reply ] };
    key <I43> { [ XF86MyComputer ] };
    key <I44> { [ XF86Documents ] };
    key <I57> { [ XF86Pictures ] };
    key <I58> { [ XF86Music ] };
    key <I5F> { [ XF86Standby ] };
    key <I65> { [ XF86Search ] };
    key <I66> {	[ XF86Favorites	] };
    key <I69> { [ XF86Forward ] };
    key <I6A> { [ XF86Back ] };
    key <I6C> { [ XF86Mail ] };
    key <I6D> { [ XF86AudioMedia ] };
};

// Logitech second set of common keys
partial hidden alphanumeric_keys
xkb_symbols "logitech_set3" {
    key <I17>	{	[ XF86AudioStop		]	};
    key <I1E>	{	[ XF86AudioRaiseVolume	]	};
    key <I1F>	{	[ XF86AudioPlay, XF86AudioPause ] };
    key <I22>	{	[ XF86AudioNext		]	};
    key <I24>	{	[ XF86AudioPrev		]	};
    key <I25>	{	[ XF86AudioLowerVolume	]	};
    key <I26>	{	[ XF86AudioMute		]	};
    key <I44>   {       [ XF86New               ]       };      // F1
    key <I45>   {       [ XF86Reply             ]       };      // F2
    key <I4A>   {       [ XF86Send              ]       };      // F4
    key <I54>   {       [ Print                 ]       };      // F7
    key <I55>   {       [ XF86Save              ]       };      // F8
    key <I56>   {       [ XF86Documents         ]       };      // F10
    key <I69>   {       [ XF86Go                ]       };
    key <XFER>  {       [ XF86AudioMedia        ]       };
};

//--------------------------------------------------------
// Logitech Cordless Desktop
partial alphanumeric_keys
xkb_symbols "ltcd" {
    include "inet(logitech_base)"
    include "inet(logitech_set3)"
};

// Logitech Access Keyboard
partial alphanumeric_keys
xkb_symbols "logiaccess" {
    include "inet(logitech_base)"

    key <FK13>	{	[ XF86MailForward	]	}; 
    key <FK14>	{	[ XF86Send		]	}; 
    key <I11>	{	[ XF86Messenger		]	};
    key <I12>	{	[ XF86WebCam		]	};
    key <I65>	{	[ XF86Search		]	}; 
};

// Logitech Cordless Desktop iTouch
partial alphanumeric_keys
xkb_symbols "logicdit" {
    include "inet(logitech_base)"
};

// Logitech Cordless Desktop Pro
partial alphanumeric_keys
xkb_symbols "logicdp" {
    include "inet(logitech_base)"

};

// Logitech Cordless Desktop Pro (alternate option)
partial alphanumeric_keys
xkb_symbols "logicdpa" {
    include "inet(logitech_base)"
    include "inet(logitech_set3)"
};

// Logitech Internet Navigator Keyboard
partial alphanumeric_keys
xkb_symbols "logicink" {
    include "inet(logitech_base)"

    key <I11>	{	[ XF86Shop		]	};
    key <I12>	{	[ XF86VendorHome	]	};
    key <I13>	{	[ XF86Finance		]	};
    key <I14>	{	[ XF86Start		]	};
};

// Logitech iTouch Internet Navigator Keyboard
partial alphanumeric_keys
xkb_symbols "logiciink" {
    include "inet(logicinc)"
};

// Logitech Cordless Desktop LX-300
partial alphanumeric_keys
xkb_symbols "logiclx300" {
    include "inet(logitech_base)"

    key <I21>	{	[ XF86Calculator	]	};
};

// Logitech iTouch Internet Navigator Keyboard SE
partial alphanumeric_keys
xkb_symbols "logiinkse" {
    include "inet(logitech_base)"

    key <FK13>	{	[ XF86MailForward	]	};	// F3
    key <FK14>	{	[ XF86Send		]	};	// F4
    key <FK15>	{	[ Undo			]	};	// F5
    key <FK16>	{	[ Redo			]	};	// F6
    key <FK17>	{	[ Print			]	};	// F7
    key <I11>	{	[ XF86Messenger		]	};
    key <I12>	{	[ XF86WebCam		]	};
    key <I13>	{	[ XF86VendorHome	]	};
    key <I14>	{	[ XF86Shop		]	};
    key <I42>	{	[ XF86Save		]	};	// F8
};

// Logitech iTouch Internet Navigator Keyboard SE (USB)
partial alphanumeric_keys
xkb_symbols "logiinkseusb" {
    include "inet(logitech_base)"
    include "inet(logitech_set3)"
};

// Logitech iTouch Cordless Keyboard (model Y-RB6)
partial alphanumeric_keys
xkb_symbols "logiitc" {
    include "inet(logitech_base)"

    key <I2F> {	[ XF86AudioRaiseVolume ] };

    // Just to override RaiseVolume from logitech_base,
    // since no keysym can have two keycodes, see
    // https://bugs.freedesktop.org/show_bug.cgi?id=7095
    key <I30> {	[ XF86Launch1 ] };
};

// Logitech Internet Keyboard
partial alphanumeric_keys
xkb_symbols "logiik" {
    include "inet(logitech_base)"

    key <I12>	{	[ Find			]	};
    key <I17>	{	[ Print			]	};
    key <I18>	{	[ XF86Favorites		]	};
    key <I19>	{	[ XF86Reload		]	};
    key <I1E>	{	[ XF86Search		]	};
    key <I20>	{	[ XF86HotLinks		]	};
    key <I22>	{	[ XF86Forward		]	};
    key <I23>	{	[ XF86HomePage		]	};
    key <I24>	{	[ XF86Stop		]	};
    key <I25>	{	[ XF86OpenURL		]	};
    key <I26>	{	[ XF86AddFavorite	]	};
    key <I32>	{	[ XF86History		]	};
    key <I7A>	{	[ XF86WWW		]	};
};

// Logitech iTouch
partial alphanumeric_keys
xkb_symbols "itouch" {
    include "inet(logitech_base)"

    key <I1F>	{	[ XF86AudioMute		]	};
    key <I2B>	{	[ XF86AudioLowerVolume	]	};
    key <I30>	{	[ XF86AudioRaiseVolume	]	};
};

partial alphanumeric_keys
xkb_symbols "logiultrax" {
    include "inet(logitech_base)"
};

partial alphanumeric_keys 
xkb_symbols "dinovo" {

    key <I02>	{	[ XF86HomePage		]	};
    key <I10>	{	[ XF86AudioPrev		]	};
    key <I12>	{	[ XF86Standby		]	};
    key <I17>	{	[ XF86Search		]	};
    key <I19>	{	[ XF86AudioNext		]	};
    key <I21>	{	[ XF86AudioRaiseVolume	]	};
    key <I22>	{	[ XF86AudioPlay, XF86AudioPause ] };
    key <I24>	{	[ XF86AudioStop		]	};
    key <I66>	{	[ XF86Start		]	};
    key <I6C>	{	[ XF86Mail		]	};
    key <K66>	{	[ XF86AudioLowerVolume	]	};
    key <KPDC>	{	[ XF86AudioMute		]	};
    key <XFER>	{	[ XF86AudioMedia	]	};
};
```

---

