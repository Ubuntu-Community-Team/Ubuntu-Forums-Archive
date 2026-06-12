---
title: "keyboard layout isn't saved"
date: 2008-04-28
forum: General Help
---

### Post by souzacds on 2008-04-28
hi,
I'm having problems with the keyboard layout under ubuntu 8.04 (under 7.10 it's not happen).
At start ubuntu, the layout is always the default US. but the keyboard settings shows the Brazilian layout. 
If I remove that layout and add again it works. But is reseted when ubuntu starts again.

Does anyone have these problem?
Or is a bug of 8.04 ?

thanks lot

---

### Post by michelux on 2008-04-29
I have the same issue with my settings although I use a US International (with dead keys) setting.
I do however see the correct keyboard, but the dead keys are not functioning until I add the "same" keyboard again.

---

### Post by grgtvs on 2008-04-30
Same problem with USA and GREEK layouts.

I just want to mention that my 8.04 installation it was an ugrade from 7.10.

---

### Post by souzacds on 2008-05-02
I`ve open this bug [https://bugs.launchpad.net/bugs/225055]("https://bugs.launchpad.net/bugs/225055")

---

### Post by ferchon03 on 2008-05-02
Same problem here with Spain layout. I have to set the keyboard layout every time I restart.
Ubuntu 8.04 clean installation.

---

### Post by iannis on 2008-05-03
Same problem with Greek layout Any Help?

---

### Post by eumetaxas on 2008-05-03
me too, greek also.
Propably had to wait before upgrading

---

### Post by ferchon03 on 2008-05-05
I've just edit /etc/X11/xorg.conf (thanks to grgtvs for the tip) and change the Option "XkbLayout" "us" for Option "XkbLayout" "es" (es=spanish) and after I restart seems to be working fine.

---

### Post by eumetaxas on 2008-05-07
updated from backports and it is ok now

---

### Post by eumetaxas on 2008-05-07
NO! got hurry again.updating did not fix.
editing the file as said above does not work for greek because it sets greek as only language which is not useful

---

### Post by grgtvs on 2008-05-08
I fixed the problem manualy by adding in the /etc/X11/xorg.conf
In the InputDevice Section

Option "XkbLayout" "us,gr" #The layouts that you want to use.
Option "XkbOptions" "grp:alt_shift_toggle" #this is for changing the layout by pressing Alt+Shift

Now it looks like

Section "InputDevice"
 Identifier "Generic Keyboard"
 Driver "kbd"
 Option "CoreKeyboard"
 Option "XkbRules" "xorg"
 Option "XkbModel" "pc105"
 Option "XkbLayout" "us,gr"
 Option "XkbOptions" "grp:alt_shift_toggle"
EndSection

and it was

Section "InputDevice"
 Identifier "Generic Keyboard"
 Driver "kbd"
 Option "CoreKeyboard"
 Option "XkbRules" "xorg"
 Option "XkbModel" "pc105"
 Option "XkbLayout" "us"
EndSection

now when i reboot my system the keyboard layout changes flawless.

This is just a workaround but the bug sustains i suppose
for new installation so it must be fixed.

---

### Post by Kralnor on 2008-05-10
> **ferchon03 said:**
> I've just edit /etc/X11/xorg.conf (thanks to grgtvs for the tip) and change the Option "XkbLayout" "us" for Option "XkbLayout" "es" (es=spanish) and after I restart seems to be working fine.

Thanks! Changing it to "dk" for danish worked for me as well.

---

### Post by JohanSwe on 2008-05-10
I assumed "sv" is for swedish but it didn't work. Also tried "us,sv". When adding sv or us,sv I get a keyboard layout with no extra characters like star os slash.

Edit the settings under Language Support in any way, gives me Swedish keyboard layout until I restart.

I got Ubuntu 8.04 and it's an upgrade.

---

### Post by JohanSwe on 2008-05-10
I found out that sv was not the right language code. I will try again and it should probably work.

Here are the languge codes (from /etc/X11/xkb/rules/xorg.lst, thanks to grgtvs):

```
! variant
  euro            us: With EuroSign on 5
  intl            us: International (with dead keys)
  alt-intl        us: Alternative international (former us_intl)
  colemak         us: Colemak
  dvorak          us: Dvorak
  dvorak-intl     us: Dvorak international
  dvorak-l        us: Left handed Dvorak
  dvorak-r        us: Right handed Dvorak
  dvorak-classic  us: Classic Dvorak
  rus             us: Russian phonetic
  mac             us: Macintosh
  altgr-intl      us: International (AltGr dead keys)
  olpc2           us: Group toggle on multiply/divide key
  ps              af: Pashto
  uz              af: Southern Uzbek
  olpc-ps         af: OLPC Pashto
  olpc-da         af: OLPC Dari
  olpc-uz         af: OLPC Southern Uzbek
  azerty          ara: azerty
  azerty_digits   ara: azerty/digits
  digits          ara: digits
  qwerty          ara: qwerty
  qwerty_digits   ara: qwerty/digits
  buckwalter      ara: Buckwalter
  phonetic        am: Phonetic
  phonetic-alt    am: Alternative Phonetic
  eastern         am: Eastern
  western         am: Western
  eastern-alt     am: Alternative Eastern
  cyrillic        az: Cyrillic
  winkeys         by: Winkeys
  latin           by: Latin
  iso-alternate   be: ISO Alternate
  nodeadkeys      be: Eliminate dead keys
  sundeadkeys     be: Sun dead keys
  wang            be: Wang model 724 azerty
  probhat         bd: Probhat
  ben             in: Bengali
  ben_probhat     in: Bengali Probhat
  guj             in: Gujarati
  guru            in: Gurmukhi
  kan             in: Kannada
  mal             in: Malayalam
  mal_lalitha     in: Malayalam Lalitha
  ori             in: Oriya
  tam_unicode     in: Tamil Unicode
  tam_TAB         in: Tamil TAB Typewriter
  tam_TSCII       in: Tamil TSCII Typewriter
  tam             in: Tamil
  tel             in: Telugu
  urd             in: Urdu
  bolnagri        in: Hindi Bolnagri
  alternatequotes ba: Use guillemets for quotes
  unicode         ba: Use Bosnian digraphs
  unicodeus       ba: US keyboard with Bosnian digraphs
  us              ba: US keyboard with Bosnian letters
  nodeadkeys      br: Eliminate dead keys
  thinkpad        br: Thinkpad
  dvorak          br: Dvorak
  nativo          br: Nativo
  nativo-us       br: Nativo for USA keyboards
  nativo-epo      br: Nativo for Esperanto
  phonetic        bg: Phonetic
  french          ma: French
  tifinagh        ma: Tifinagh
  tifinagh-alt    ma: Tifinagh Alternative
  tifinagh-alt-phonetic ma: Tifinagh Alternative Phonetic
  tifinagh-extended ma: Tifinagh Extended
  tifinagh-phonetic ma: Tifinagh Phonetic
  tifinagh-extended-phonetic ma: Tifinagh Extended Phonetic
  fr-dvorak       ca: French Dvorak
  fr-legacy       ca: French (legacy)
  multix          ca: Multilingual
  multi           ca: Multilingual, first part
  multi-2gr       ca: Multilingual, second part
  ike             ca: Inuktitut
  shs             ca: Secwepemctsin
  tib             cn: Tibetan
  tib_asciinum    cn: Tibetan (with ASCII numerals)
  alternatequotes hr: Use guillemets for quotes
  unicode         hr: Use Croatian digraphs
  unicodeus       hr: US keyboard with Croatian digraphs
  us              hr: US keyboard with Croatian letters
  bksl            cz: With &lt;\|&gt; key
  qwerty          cz: qwerty
  qwerty_bksl     cz: qwerty, extended Backslash
  nodeadkeys      dk: Eliminate dead keys
  mac             dk: Macintosh
  mac_nodeadkeys  dk: Macintosh, eliminate dead keys
  dvorak          dk: Dvorak
  sundeadkeys     nl: Sun dead keys
  mac             nl: Macintosh
  std             nl: Standard
  nodeadkeys      ee: Eliminate dead keys
  dvorak          ee: Dvorak
  us              ee: US keyboard with Estonian letters
  pro             ir: Pro
  keypad          ir: Keypad
  pro_keypad      ir: Pro Keypad
  ku              ir: Kurdish, Latin Q
  ku_f            ir: Kurdish, (F)
  ku_alt          ir: Kurdish, Latin Alt-Q
  ku_ara          ir: Kurdish, Arabic-Latin
  ku              iq: Kurdish, Latin Q
  ku_f            iq: Kurdish, (F)
  ku_alt          iq: Kurdish, Latin Alt-Q
  ku_ara          iq: Kurdish, Arabic-Latin
  nodeadkeys      fo: Eliminate dead keys
  nodeadkeys      fi: Eliminate dead keys
  smi             fi: Northern Saami
  classic         fi: Classic
  mac             fi: Macintosh
  nodeadkeys      fr: Eliminate dead keys
  sundeadkeys     fr: Sun dead keys
  oss             fr: Alternative
  oss_latin9      fr: Alternative, latin-9 only
  oss_nodeadkeys  fr: Alternative, eliminate dead keys
  oss_sundeadkeys fr: Alternative, Sun dead keys
  latin9          fr: (Legacy) Alternative
  latin9_nodeadkeys fr: (Legacy) Alternative, eliminate dead keys
  latin9_sundeadkeys fr: (Legacy) Alternative, Sun dead keys
  bepo            fr: Bepo, ergonomic, Dvorak way
  bepo_latin9     fr: Bepo, ergonomic, Dvorak way, latin-9 only
  dvorak          fr: (Legacy) Dvorak
  mac             fr: Macintosh
  geo             fr: Georgian AZERTY Tskapo
  generic         gh: Multilingual
  akan            gh: Akan
  ewe             gh: Ewe
  fula            gh: Fula
  ga              gh: Ga
  hausa           gh: Hausa
  ergonomic       ge: Ergonomic
  mess            ge: MESS
  ru              ge: Russian
  os              ge: Ossetian
  deadacute       de: Dead acute
  deadgraveacute  de: Dead grave acute
  nodeadkeys      de: Eliminate dead keys
  ro              de: Romanian keyboard with German letters
  ro_nodeadkeys   de: Romanian keyboard with German letters, eliminate dead keys
  dvorak          de: Dvorak
  sundeadkeys     de: Sun dead keys
  neo             de: Neostyle
  mac             de: Macintosh
  mac_nodeadkeys  de: Macintosh, eliminate dead keys
  extended        gr: Extended
  nodeadkeys      gr: Eliminate dead keys
  polytonic       gr: Polytonic
  standard        hu: Standard
  nodeadkeys      hu: Eliminate dead keys
  qwerty          hu: qwerty
  101_qwertz_comma_dead hu: 101/qwertz/comma/Dead keys
  101_qwertz_comma_nodead hu: 101/qwertz/comma/Eliminate dead keys
  101_qwertz_dot_dead hu: 101/qwertz/dot/Dead keys
  101_qwertz_dot_nodead hu: 101/qwertz/dot/Eliminate dead keys
  101_qwerty_comma_dead hu: 101/qwerty/comma/Dead keys
  101_qwerty_comma_nodead hu: 101/qwerty/comma/Eliminate dead keys
  101_qwerty_dot_dead hu: 101/qwerty/dot/Dead keys
  101_qwerty_dot_nodead hu: 101/qwerty/dot/Eliminate dead keys
  102_qwertz_comma_dead hu: 102/qwertz/comma/Dead keys
  102_qwertz_comma_nodead hu: 102/qwertz/comma/Eliminate dead keys
  102_qwertz_dot_dead hu: 102/qwertz/dot/Dead keys
  102_qwertz_dot_nodead hu: 102/qwertz/dot/Eliminate dead keys
  102_qwerty_comma_dead hu: 102/qwerty/comma/Dead keys
  102_qwerty_comma_nodead hu: 102/qwerty/comma/Eliminate dead keys
  102_qwerty_dot_dead hu: 102/qwerty/dot/Dead keys
  102_qwerty_dot_nodead hu: 102/qwerty/dot/Eliminate dead keys
  Sundeadkeys     is: Sun dead keys
  nodeadkeys      is: Eliminate dead keys
  mac             is: Macintosh
  lyx             il: lyx
  phonetic        il: Phonetic
  biblical        il: Biblical Hebrew (Tiro)
  nodeadkeys      it: Eliminate dead keys
  mac             it: Macintosh
  geo             it: Georgian
  kana            jp: Kana
  OADG109A        jp: OADG 109A
  ruskaz          kz: Russian with Kazakh
  kazrus          kz: Kazakh with Russian
  nodeadkeys      latam: Eliminate dead keys
  sundeadkeys     latam: Sun dead keys
  std             lt: Standard
  us              lt: US keyboard with Lithuanian letters
  ibm             lt: IBM (LST 1205-92)
  apostrophe      lv: Apostrophe (') variant
  tilde           lv: Tilde (~) variant
  fkey            lv: F-letter (F) variant
  cyrillic        me: Cyrillic
  cyrillicyz      me: Cyrillic, Z and ZHE swapped
  latinunicode    me: Latin unicode
  latinyz         me: Latin qwerty
  latinunicodeyz  me: Latin unicode qwerty
  cyrillicalternatequotes me: Cyrillic with guillemets
  latinalternatequotes me: Latin with guillemets
  nodeadkeys      mk: Eliminate dead keys
  us              mt: Maltese keyboard with US layout
  nodeadkeys      no: Eliminate dead keys
  dvorak          no: Dvorak
  smi             no: Northern Saami
  smi_nodeadkeys  no: Northern Saami, eliminate dead keys
  mac             no: Macintosh
  mac_nodeadkeys  no: Macintosh, eliminate dead keys
  qwertz          pl: qwertz
  dvorak          pl: Dvorak
  dvorak_quotes   pl: Dvorak, Polish quotes on quotemark key
  dvorak_altquotes pl: Dvorak, Polish quotes on key "1/!"
  csb             pl: Kashubian
  ru_phonetic_dvorak pl: Russian phonetic Dvorak
  nodeadkeys      pt: Eliminate dead keys
  sundeadkeys     pt: Sun dead keys
  mac             pt: Macintosh
  mac_nodeadkeys  pt: Macintosh, eliminate dead keys
  mac_sundeadkeys pt: Macintosh, Sun dead keys
  nativo          pt: Nativo
  nativo-us       pt: Nativo for USA keyboards
  nativo-epo      pt: Nativo for Esperanto
  comma           ro: Commabelow
  std_comma       ro: Standard (Commabelow)
  std_cedilla     ro: Standard (Cedilla)
  winkeys         ro: Winkeys
  phonetic        ru: Phonetic
  typewriter      ru: Typewriter
  winkeys         ru: Winkeys
  tt              ru: Tatar
  os              ru: Ossetian
  os_winkeys      ru: Ossetian, Winkeys
  cv              ru: Chuvash
  cv_latin        ru: Chuvash Latin
  udm             ru: Udmurt
  kom             ru: Komi
  yz              rs: Z and ZHE swapped
  latin           rs: Latin
  latinunicode    rs: Latin Unicode
  latinyz         rs: Latin qwerty
  latinunicodeyz  rs: Latin Unicode qwerty
  alternatequotes rs: With guillemets
  latinalternatequotes rs: Latin with guillemets
  alternatequotes si: Use guillemets for quotes
  unicode         si: Use Slovenian digraphs
  unicodeus       si: US keyboard with Slovenian digraphs
  us              si: US keyboard with Slovenian letters
  bksl            sk: Extended Backslash
  qwerty          sk: qwerty
  qwerty_bksl     sk: qwerty, extended Backslash
  nodeadkeys      es: Eliminate dead keys
  sundeadkeys     es: Sun dead keys
  dvorak          es: Dvorak
  cat             es: Catalan variant with middle-dot L
  mac             es: Macintosh
  nodeadkeys      se: Eliminate dead keys
  dvorak          se: Dvorak
  rus             se: Russian phonetic
  rus_nodeadkeys  se: Russian phonetic, eliminate dead keys
  smi             se: Northern Saami
  mac             se: Macintosh
  svdvorak        se: Svdvorak
  de_nodeadkeys   ch: German, eliminate dead keys
  de_sundeadkeys  ch: German, Sun dead keys
  fr              ch: French
  fr_nodeadkeys   ch: French, eliminate dead keys
  fr_sundeadkeys  ch: French, Sun dead keys
  fr_mac          ch: French (Macintosh)
  de_mac          ch: German (Macintosh)
  syc             sy: Syriac
  syc_phonetic    sy: Syriac phonetic
  ku              sy: Kurdish, Latin Q
  ku_f            sy: Kurdish, (F)
  ku_alt          sy: Kurdish, Latin Alt-Q
  tam_unicode     lk: Tamil Unicode
  tam_TAB         lk: Tamil TAB Typewriter
  tis             th: TIS-820.2538
  pat             th: Pattachote
  f               tr: (F)
  alt             tr: Alt-Q
  sundeadkeys     tr: Sun dead keys
  ku              tr: Kurdish, Latin Q
  ku_f            tr: Kurdish, (F)
  ku_alt          tr: Kurdish, Latin Alt-Q
  intl            tr: International (with dead keys)
  phonetic        ua: Phonetic
  typewriter      ua: Typewriter
  winkeys         ua: Winkeys
  unicode         ua: Unicode
  rstu            ua: Standard RSTU
  rstu_ru         ua: Standard RSTU on Russian layout
  intl            gb: International (with dead keys)
  dvorak          gb: Dvorak
  mac             gb: Macintosh
  latin           uz: Latin
  kr104           kr: 101/104 key Compatible
  CloGaelach      ie: CloGaelach
  UnicodeExpert   ie: UnicodeExpert
  ogam            ie: Ogham
  ogam_is434      ie: Ogham IS434
  ara             pk: Arabic
  legacy          epo: displaced semicolon and quote (obsolete)
  igbo            ng: Igbo
  yoruba          ng: Yoruba
  hausa           ng: Hausa
  left_hand       braille: Left hand
  right_hand      braille: Right hand
```

---

### Post by cmavr8 on 2008-05-11
Well done grgtvs!
Works perfectly for me too!

Zito i Hellas!

---

### Post by grgtvs on 2008-05-12
> **cmavr8 said:**
> Well done grgtvs!
Works perfectly for me too!

Zito i Hellas!

:) Zito!!!

---

### Post by Thanoulis on 2008-05-12
Hey you guys!
Try to run *setxkbmap* in the startup session...after that EVERYTHING works fine...even the keyboard layout applet!!! :)

---

### Post by brallan on 2008-09-08
wow, that worked great! thanks!

---

### Post by simosx on 2008-09-09
It's a known bug that has been fixed upstream. 
The fix will make it in Ubuntu 8.10, but at the moment I do not think there are updated packages for 8.04.

In general terms, this problem happens when you have Autologin enabled. If autologin is not enabled, you are OK.

---

### Post by Johann-1.0 on 2010-05-21
JohanSwe, can you tell me how modify the keyboard variant?
For example: I'm using latam and ru, but I want ru to be as phonetic and typewriter variant. How can I do that?
I was thinking something like:

Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc105"
    Option        "XkbLayout"    "latam, ru, ru"
    Option        "XkbVariant"    " , Phonetic, Typewriter "
Is it possible? How can I do with the latam?
Thanks in advance my friend.

---

