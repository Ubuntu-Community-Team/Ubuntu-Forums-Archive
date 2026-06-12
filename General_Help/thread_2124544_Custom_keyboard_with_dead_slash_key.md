---
title: "Custom keyboard with dead slash key"
date: 2013-03-11
forum: General Help
---

### Post by ptoche on 2013-03-11
Dear all,

I am writing a customized keyboard layout. I have kUbuntu 12.10 and have successfully got the layout recognized. My question is about how to achieve specific key combinations.

I would like to make the slash and backslash into dead keys that combine with letters in the same way as dead_acute and dead_grave, as in:

```

 dead_slash + a = à
 dead_backslash + a =  á

```

I did that on my Windows machines using the Microsoft Keyboard Layout Creator and would now like to have it on my Ubuntu system.

I have managed the more straightforward mapping (see my test layout immediately below):
```

 dead_grave + a = à
 dead_acute + a =  á

```

The following is my xkb test layout. 

```

partial alphanumeric_keys
xkb_symbols "dv" {

  name[Group1]= "myDvorak";

  include "us(dvorak)"

  key <AD11> {[ dead_acute ]};
  key <AD12> {[ dead_grave ]};

  include "level3(ralt_switch)"

};

```

Naturally, I did try dead_slash instead of dead_acute and dead_backslash instead of dead_grave, but that failed.

In words, what I'd like to achieve is this: 


[LIST]
[*]type the slash key once followed by the letter a and get à.
[*]type the slash key twice and get a slash
[/LIST]

I'd appreciate suggestions.   

Thanks.

N.B. This is a repeat of my stackoverflow question which has so far generated no replies:
[http://stackoverflow.com/questions/15308809/xkb-keyboard-layout-with-slash-as-a-dead-key](http://stackoverflow.com/questions/15308809/xkb-keyboard-layout-with-slash-as-a-dead-key)

---

