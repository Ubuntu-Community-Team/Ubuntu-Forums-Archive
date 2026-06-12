---
title: "Unable to map right Win-key to CTRL"
date: 2007-02-01
forum: General Help
---

### Post by kakadu on 2007-02-01
Hi. My mini keyboard doesnt have right CTRL key, but instad it has Win and Menu keys which I dont use, so I wanted to map Win-key to CTRL with "xmodmap".
First to findout that key code, with `xmodmap -pke` I've got this:
```

keycode   8 =
keycode   9 = Escape
keycode  10 = 1 exclam 1 exclam dead_tilde asciitilde 1 exclam dead_tilde asciitilde
keycode  11 = 2 at 2 quotedbl dead_caron caron 2 quotedbl dead_caron caron
keycode  12 = 3 numbersign 3 numbersign dead_circumflex asciicircum 3 numbersign dead_circumflex asciicircum
keycode  13 = 4 dollar 4 dollar dead_breve breve 4 dollar dead_breve breve
keycode  14 = 5 percent 5 percent dead_abovering degree 5 percent dead_abovering degree
keycode  15 = 6 asciicircum 6 ampersand dead_ogonek ogonek 6 ampersand dead_ogonek ogonek
keycode  16 = 7 ampersand 7 slash dead_grave grave 7 slash dead_grave grave
keycode  17 = 8 asterisk 8 parenleft dead_abovedot abovedot 8 parenleft dead_abovedot abovedot
keycode  18 = 9 parenleft 9 parenright dead_acute apostrophe 9 parenright dead_acute apostrophe
keycode  19 = 0 parenright 0 equal dead_doubleacute doubleacute 0 equal dead_doubleacute doubleacute
keycode  20 = minus underscore apostrophe question dead_diaeresis diaeresis apostrophe question dead_diaeresis diaeresis
keycode  21 = equal plus plus asterisk dead_cedilla cedilla plus asterisk dead_cedilla cedilla
keycode  22 = BackSpace Terminate_Server
keycode  23 = Tab ISO_Left_Tab
keycode  24 = q Q Cyrillic_lje Cyrillic_LJE backslash Greek_OMEGA q Q backslash Greek_OMEGA
keycode  25 = w W Cyrillic_nje Cyrillic_NJE bar Lstroke w W bar Lstroke
keycode  26 = e E Cyrillic_ie Cyrillic_IE EuroSign EuroSign e E EuroSign EuroSign
keycode  27 = r R Cyrillic_er Cyrillic_ER paragraph registered r R paragraph registered
keycode  28 = t T Cyrillic_te Cyrillic_TE tslash Tslash t T tslash Tslash
keycode  29 = y Y Cyrillic_ze Cyrillic_ZE leftarrow yen z Z leftarrow yen
keycode  30 = u U Cyrillic_u Cyrillic_U downarrow uparrow u U downarrow uparrow
keycode  31 = i I Cyrillic_i Cyrillic_I rightarrow idotless i I rightarrow idotless
keycode  32 = o O Cyrillic_o Cyrillic_O oslash Oslash o O oslash Oslash
keycode  33 = p P Cyrillic_pe Cyrillic_PE thorn THORN p P thorn THORN
keycode  34 = bracketleft braceleft Cyrillic_sha Cyrillic_SHA division dead_abovering scaron Scaron division dead_abovering
keycode  35 = bracketright braceright Serbian_dje Serbian_DJE multiply dead_macron dstroke Dstroke multiply dead_macron
keycode  36 = Return
keycode  37 = Control_L
keycode  38 = a A Cyrillic_a Cyrillic_A ae AE a A ae AE
keycode  39 = s S Cyrillic_es Cyrillic_ES doublelowquotemark guillemotright s S doublelowquotemark guillemotright
keycode  40 = d D Cyrillic_de Cyrillic_DE leftdoublequotemark guillemotleft d D leftdoublequotemark guillemotleft
keycode  41 = f F Cyrillic_ef Cyrillic_EF bracketleft ordfeminine f F bracketleft ordfeminine
keycode  42 = g G Cyrillic_ghe Cyrillic_GHE bracketright ENG g G bracketright ENG
keycode  43 = h H Cyrillic_ha Cyrillic_HA hstroke Hstroke h H hstroke Hstroke
keycode  44 = j J Cyrillic_je Cyrillic_JE NoSymbol NoSymbol j J
keycode  45 = k K Cyrillic_ka Cyrillic_KA lstroke ampersand k K lstroke ampersand
keycode  46 = l L Cyrillic_el Cyrillic_EL lstroke Lstroke l L lstroke Lstroke
keycode  47 = semicolon colon Cyrillic_che Cyrillic_CHE dead_acute dead_doubleacute ccaron Ccaron dead_acute dead_doubleacute
keycode  48 = apostrophe quotedbl Serbian_tshe Serbian_TSHE ssharp dead_caron cacute Cacute ssharp dead_caron
keycode  49 = grave asciitilde grave asciitilde notsign notsign grave asciitilde notsign notsign
keycode  50 = Shift_L ISO_Prev_Group
keycode  51 = backslash bar Cyrillic_zhe Cyrillic_ZHE currency dead_breve zcaron Zcaron currency dead_breve
keycode  52 = z Z Cyrillic_zhe Cyrillic_ZHE leftsinglequotemark guillemotright y Y leftsinglequotemark guillemotright
keycode  53 = x X Cyrillic_dzhe Cyrillic_DZHE rightsinglequotemark guillemotleft x X rightsinglequotemark guillemotleft
keycode  54 = c C Cyrillic_tse Cyrillic_TSE cent copyright c C cent copyright
keycode  55 = v V Cyrillic_ve Cyrillic_VE at grave v V at grave
keycode  56 = b B Cyrillic_be Cyrillic_BE braceleft apostrophe b B braceleft apostrophe
keycode  57 = n N Cyrillic_en Cyrillic_EN braceright braceright n N braceright braceright
keycode  58 = m M Cyrillic_em Cyrillic_EM asciicircum masculine m M asciicircum masculine
keycode  59 = comma less comma semicolon less multiply comma semicolon less multiply
keycode  60 = period greater period colon greater division period colon greater division
keycode  61 = slash question minus underscore emdash endash minus underscore emdash endash
keycode  62 = Shift_R ISO_Next_Group
keycode  63 = KP_Multiply XF86_ClearGrab
keycode  64 = Alt_L Meta_L
keycode  65 = space
keycode  66 = Caps_Lock
keycode  67 = F1 XF86_Switch_VT_1
keycode  68 = F2 XF86_Switch_VT_2
keycode  69 = F3 XF86_Switch_VT_3
keycode  70 = F4 XF86_Switch_VT_4
keycode  71 = Control_R
keycode  72 = F6 XF86_Switch_VT_6
keycode  73 = F7 XF86_Switch_VT_7
keycode  74 = F8 XF86_Switch_VT_8
keycode  75 = F9 XF86_Switch_VT_9
keycode  76 = F10 XF86_Switch_VT_10
keycode  77 = Num_Lock
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
keycode  91 = KP_Delete KP_Decimal KP_Delete KP_Separator KP_Delete KP_Separator
keycode  92 =
keycode  93 = Mode_switch
keycode  94 = less greater bar brokenbar bar brokenbar
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
keycode 113 = Alt_R Meta_R ISO_Level3_Shift NoSymbol ISO_Level3_Shift
keycode 114 =
keycode 115 = Super_L
keycode 116 = Control_L
keycode 117 = Control_R
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

```
After this, I've noticed that coresponding key code is "116" so I've tried `xmodmap -e 'keycode 116 = Control_R'` (and later `xmodmap -e 'keycode 116 = Control_L'`) but with no effect, for example if I press (original) CTRL+a it puts cursor at start of the line, but if I try that with newly mapped key it only outputs 'a'. Interestingly enough if I try to map that Win-key to ALT with `xmodmap -e 'keycode 116 = Alt_R'` it has effect and it _does_ behave like ordinary ALT key.

Can someone please tell me how can I map right (or both if there is too much work) Win-key which I dont use, to CTRL?

Thanks in advance.

---

### Post by kakadu on 2007-02-03
Anyone please?

---

### Post by kakadu on 2007-02-06
Problem solved.

For anyone who might be interested in the solution, please visit this discussion: [http://www.linuxquestions.org/questions/showthread.php?p=2611981](http://www.linuxquestions.org/questions/showthread.php?p=2611981)

---

