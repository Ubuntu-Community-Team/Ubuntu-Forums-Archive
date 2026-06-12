---
title: "keyboard problem. Suspect X prblem. HELP"
date: 2007-11-14
forum: General Help
---

### Post by lord-castigamatti on 2007-11-14
hi. i installed the gutsy gibbon 7.10 and all work fine until now.

yesterday, after install footballmanager 2008 with wine (work good!!!) but now The keyboard characters are all reversed. i suppose is a X problem because when i run in terminal (not the graphic mode) keyboard work good also in the login screen after the splash screen work good. 

:confused::confused::confused:

I am really confused and I hope your help in that forum Italian (I am Italian) nobody knew answer

I apologize for my English but it is the best I can do

thank u

lord-castigamatti

---

### Post by bingoUV on 2007-11-14
I am assuming you are using standard American keyboard layout. If not, please post your keyboard layout that you chose during install.

What do you mean by keyboard characters are reversed? 
1. Typing Q produces P ? 
2. Or typing Q produces Z?
3. Or typing M produces W?
4. Or upper case has become lower case?
5. Typing A produces Z, B produces Y etc.?

Post the output of the following command
```

xmodmap -pke

```

---

### Post by lord-castigamatti on 2007-11-14
i am at university now without laptop. Upon arrival at home I spot what you asked me. However, keyboard should be corrected. typing o, is 6 and, in general, many letters are replaced by numbers. But I do not think it is a problem of keyboard settings as I wrote in my first post as from terminal (non-graphical) works well. 

PS I wrote in the section right? As i am new user, is always better to ask ..

---

### Post by bingoUV on 2007-11-14
In menu System -> Preferences -> Keyboard -> Layouts,
choose a layout that works properly for you.

---

### Post by lord-castigamatti on 2007-11-15
it's not layout problem. this is the only thing i know. i have already test other layouts but doesn't work. 

Is possible that anyone know the problem?

keyboard problem are only layout problem? i guess not...

thank u all. i wait an answer

---

### Post by bingoUV on 2007-11-15
you did not give the output of the command 
```

xmodmap -pke

```

---

### Post by lord-castigamatti on 2007-11-15
this is the result for the command

xmodmap -pke

what do u think? any news?

```
bona@lord-castigamatti:~$ xmodmap -pke 
keycode   8 = 
keycode   9 = Escape 
keycode  10 = 1 exclam onesuperior exclamdown onesuperior exclamdown 
keycode  11 = 2 quotedbl twosuperior doubleacute twosuperior doubleacute 
keycode  12 = 3 sterling threesuperior asciitilde threesuperior asciitilde 
keycode  13 = 4 dollar onequarter oneeighth onequarter oneeighth 
keycode  14 = 5 percent onehalf threeeighths onehalf threeeighths 
keycode  15 = 6 ampersand notsign fiveeighths notsign fiveeighths 
keycode  16 = 7 slash braceleft seveneighths braceleft seveneighths 
keycode  17 = 8 parenleft bracketleft trademark bracketleft trademark 
keycode  18 = 9 parenright bracketright plusminus bracketright plusminus 
keycode  19 = 0 equal braceright ogonek braceright ogonek 
keycode  20 = apostrophe question grave questiondown grave questiondown 
keycode  21 = igrave asciicircum asciitilde asciicircum asciitilde asciicircum 
keycode  22 = BackSpace Terminate_Server 
keycode  23 = Tab ISO_Left_Tab 
keycode  24 = q Q at Greek_OMEGA at Greek_OMEGA 
keycode  25 = w W lstroke Lstroke lstroke Lstroke 
keycode  26 = e E EuroSign cent EuroSign cent 
keycode  27 = r R paragraph registered paragraph registered 
keycode  28 = t T tslash Tslash tslash Tslash 
keycode  29 = y Y leftarrow yen leftarrow yen 
keycode  30 = u U downarrow uparrow downarrow uparrow 
keycode  31 = i I rightarrow idotless rightarrow idotless 
keycode  32 = o O oslash Oslash oslash Oslash 
keycode  33 = p P thorn THORN thorn THORN 
keycode  34 = egrave eacute bracketleft braceleft bracketleft braceleft 
keycode  35 = plus asterisk bracketright braceright bracketright braceright 
keycode  36 = Return 
keycode  37 = Control_L 
keycode  38 = a A ae AE ae AE 
keycode  39 = s S ssharp section ssharp section 
keycode  40 = d D eth ETH eth ETH 
keycode  41 = f F dstroke ordfeminine dstroke ordfeminine 
keycode  42 = g G eng ENG eng ENG 
keycode  43 = h H hstroke Hstroke hstroke Hstroke 
keycode  44 = j J 
keycode  45 = k K kra ampersand kra ampersand 
keycode  46 = l L lstroke Lstroke lstroke Lstroke 
keycode  47 = ograve ccedilla at cedilla at cedilla 
keycode  48 = agrave degree numbersign degree numbersign degree 
keycode  49 = backslash bar notsign brokenbar notsign brokenbar 
keycode  50 = Shift_L 
keycode  51 = ugrave section grave breve grave breve 
keycode  52 = z Z guillemotleft less guillemotleft less 
keycode  53 = x X guillemotright greater guillemotright greater 
keycode  54 = c C cent copyright cent copyright 
keycode  55 = v V leftdoublequotemark leftsinglequotemark leftdoublequotemark leftsinglequotemark 
keycode  56 = b B rightdoublequotemark rightsinglequotemark rightdoublequotemark rightsinglequotemark 
keycode  57 = n N ntilde Ntilde ntilde Ntilde 
keycode  58 = m M mu masculine mu masculine 
keycode  59 = comma semicolon acute multiply acute multiply 
keycode  60 = period colon periodcentered diaeresis periodcentered diaeresis 
keycode  61 = minus underscore macron division macron division 
keycode  62 = Shift_R 
keycode  63 = KP_Multiply XF86_ClearGrab 
keycode  64 = Alt_L ISO_Prev_Group ISO_Prev_Group NoSymbol ISO_Prev_Group 
keycode  65 = space 
keycode  66 = Caps_Lock 
keycode  67 = F1 XF86_Switch_VT_1 
keycode  68 = F2 XF86_Switch_VT_2 
keycode  69 = F3 XF86_Switch_VT_3 
keycode  70 = F4 XF86_Switch_VT_4 
keycode  71 = F5 XF86_Switch_VT_5 
keycode  72 = F6 XF86_Switch_VT_6 
keycode  73 = F7 XF86_Switch_VT_7 
keycode  74 = F8 XF86_Switch_VT_8 
keycode  75 = F9 XF86_Switch_VT_9 
keycode  76 = F10 XF86_Switch_VT_10 
keycode  77 = Num_Lock Pointer_EnableKeys 
keycode  78 = Scroll_Lock 
keycode  79 = KP_Home KP_7 
keycode  80 = KP_Up KP_8 
keycode  81 = KP_Prior KP_9 
keycode  82 = KP_Subtract XF86_Prev_VMode 
keycode  83 = KP_Left KP_4 
keycode  84 = KP_Begin KP_5 
keycode  85 = KP_Right KP_6 
keycode  86 = KP_Add XF86_Next_VMode 
keycode  87 = KP_End KP_1 
keycode  88 = KP_Down KP_2 
keycode  89 = KP_Next KP_3 
keycode  90 = KP_Insert KP_0 
keycode  91 = KP_Delete KP_Decimal 
keycode  92 = 
keycode  93 = Mode_switch 
keycode  94 = less greater guillemotleft guillemotright guillemotleft guillemotright 
keycode  95 = F11 XF86_Switch_VT_11 
keycode  96 = F12 XF86_Switch_VT_12 
keycode  97 = Home 
keycode  98 = Up 
keycode  99 = Prior 
keycode 100 = Left 
keycode 101 = 
keycode 102 = Right 
keycode 103 = End 
keycode 104 = Down 
keycode 105 = Next 
keycode 106 = Insert 
keycode 107 = Delete 
keycode 108 = KP_Enter 
keycode 109 = Control_R 
keycode 110 = Pause Break 
keycode 111 = Print Sys_Req 
keycode 112 = KP_Divide XF86_Ungrab 
keycode 113 = ISO_Level3_Shift ISO_Next_Group 
keycode 114 = 
keycode 115 = Super_L 
keycode 116 = Super_R 
keycode 117 = Menu 
keycode 118 = 
keycode 119 = 
keycode 120 = 
keycode 121 = 
keycode 122 = 
keycode 123 = 
keycode 124 = ISO_Level3_Shift 
keycode 125 = NoSymbol Alt_L 
keycode 126 = KP_Equal 
keycode 127 = NoSymbol Super_L 
keycode 128 = NoSymbol Hyper_L 
keycode 129 = 
keycode 130 = 
keycode 131 = 
keycode 132 = 
keycode 133 = 
keycode 134 = 
keycode 135 = 
keycode 136 = 
keycode 137 = 
keycode 138 = 
keycode 139 = 
keycode 140 = 
keycode 141 = 
keycode 142 = 
keycode 143 = 
keycode 144 = 
keycode 145 = 
keycode 146 = 
keycode 147 = 
keycode 148 = 
keycode 149 = 
keycode 150 = 
keycode 151 = 
keycode 152 = 
keycode 153 = 
keycode 154 = 
keycode 155 = 
keycode 156 = NoSymbol Meta_L 
keycode 157 = 
keycode 158 = 
keycode 159 = 
keycode 160 = 
keycode 161 = 
keycode 162 = 
keycode 163 = 
keycode 164 = 
keycode 165 = 
keycode 166 = 
keycode 167 = 
keycode 168 = 
keycode 169 = 
keycode 170 = 
keycode 171 = 
keycode 172 = 
keycode 173 = 
keycode 174 = 
keycode 175 = 
keycode 176 = 
keycode 177 = 
keycode 178 = 
keycode 179 = 
keycode 180 = 
keycode 181 = 
keycode 182 = 
keycode 183 = 
keycode 184 = 
keycode 185 = 
keycode 186 = 
keycode 187 = 
keycode 188 = 
keycode 189 = 
keycode 190 = 
keycode 191 = 
keycode 192 = 
keycode 193 = 
keycode 194 = 
keycode 195 = 
keycode 196 = 
keycode 197 = 
keycode 198 = 
keycode 199 = 
keycode 200 = 
keycode 201 = 
keycode 202 = 
keycode 203 = 
keycode 204 = 
keycode 205 = 
keycode 206 = 
keycode 207 = 
keycode 208 = 
keycode 209 = 
keycode 210 = 
keycode 211 = 
keycode 212 = 
keycode 213 = 
keycode 214 = 
keycode 215 = 
keycode 216 = 
keycode 217 = 
keycode 218 = 
keycode 219 = 
keycode 220 = 
keycode 221 = 
keycode 222 = 
keycode 223 = 
keycode 224 = 
keycode 225 = 
keycode 226 = 
keycode 227 = 
keycode 228 = 
keycode 229 = 
keycode 230 = 
keycode 231 = 
keycode 232 = 
keycode 233 = 
keycode 234 = 
keycode 235 = 
keycode 236 = 
keycode 237 = 
keycode 238 = 
keycode 239 = 
keycode 240 = 
keycode 241 = 
keycode 242 = 
keycode 243 = 
keycode 244 = 
keycode 245 = 
keycode 246 = 
keycode 247 = 
keycode 248 = 
keycode 249 = 
keycode 250 = 
keycode 251 = 
keycode 252 = 
keycode 253 = 
keycode 254 = 
keycode 255 = 
bona@lord-castigamatti:~$  

```

---

### Post by ursi on 2007-11-15
I am having trouble with my laptop keyboard with same program install. When I type fast, my letters in one word are jumping back two words. WTF?:confused:

Sony Viao. Ubuntu,

---

### Post by lord-castigamatti on 2007-11-16
bingoUV u disappear?

i post what u want. please help me...

---

### Post by lord-castigamatti on 2007-11-16
no one can help me?

u can't force me to return vista right?

---

### Post by bingoUV on 2007-11-16
> **lord-castigamatti said:**
> bingoUV u disappear?

i post what u want. please help me...

Sorry. The output seems OK. A part of it deals with accented characters, which is absent from my settings, but I guess that should be fine. We will suspect it later. 

For now, pick any of your keys that do not produce the desired outcome, say X. Start xev in your graphical session, and press that key X. Note the keycode and keysym generated by that key. Report your observation.

---

### Post by lord-castigamatti on 2007-11-19
I decided to format because the length of operations for the restoration of the keyboard settings. 
I regret having been defeated by "X"..   but now put in the new installation ati drivers went out for my video card and I hope everything works.

Thanks bingo UV ... You were the only one who tried to help.

The next problem .. We hope that there is never ...

---

### Post by lord-castigamatti on 2007-11-19
I forgot .. I had a problem in the old setup, and that persists in the new. Ubuntu works only when connected to the electricity grid. Powered by battery fails splash.
My laptop is a asus x50 do not know if anyone else has had the same problem. In what section must post the problem?

---

