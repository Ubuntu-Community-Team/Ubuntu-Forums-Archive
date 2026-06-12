---
title: "what input for UTF-8/Unicode in bash?"
date: 2019-12-28
forum: General Help
---

### Post by Skaperen on 2019-12-28
i want to type in, or assign to a variable to be expanded in a command, some kind of sequence that gets expanded to the bytes of a UTF-8 sequence or a Unicode value.  i have a file that has UTF-8 in its name.  a list of file names will be output.  i want to filter these names with one of the grep commands.  can this be done?

---

### Post by dragonfly41 on 2019-12-28
To search for strings *inside* files I use [ripgrep]("https://github.com/BurntSushi/ripgrep").

P.S. Here is a [ripgrep wrapper]("https://www.machine-learning.news/example/21479762") for various file types.

---

### Post by Skaperen on 2019-12-29
filtering file names is just one example of the use of inputting unicode and/or utf-8 in bash.  sorry i didn't make that clear.  how to do the input is my goal, from knowing the numeric codes for these characters, such as searching for "&#1042;&#1083;&#1072;&#1076;&#1080;&#1084;&#1080;&#1088; &#1055;&#1091;&#1090;&#1080;&#1085;" but not being able to type or paste these characters in.

---

### Post by Impavidus on 2019-12-30
If you have the numeric codes of the characters and want to type them in a terminal (or many other applications), use ctrl+shift+u, [numeric code in hexadecimal], <space>. What shell or other application is running in the terminal is irrelevant (most of the time), as the input is handled by the terminal, which converts it to UTF-8 encoded strings, which are passed to the application running inside.

Most naïve applications/tools/library funtions designed to handle ASCII can handle UTF-8 without modification. That's how UTF-8 was designed. The only real change is that counting characters has become different from counting bytes.

Instead of learning all numeric codes by heart, you can often use the compose key (for symbols, accented characters or characters derived from ordinary letters) or switch keyboard layout (for a completely different alphabet).

---

### Post by The Cog on 2019-12-30
Also: 
You don't need to type the leading zeros in Ctrl+Shift+U [hex-number] <space>.
There is a fascinating app called Character Map (binary name **gucharmap**) that shows all unicode characters, and you can double-click characters to put them in a copyable text field at the bottom.

---

### Post by Skaperen on 2019-12-30
[COLOR=#0000cd][/COLOR]i think i'm going to set a keyboard shortcut (hot key) to start [COLOR=#0000cd]**gucharmap**[/COLOR].

i just tried ctrl+shift+u with a code and just got the unconverted ascii character, starting with the u in lower case.  this was with [COLOR=#0000cd][FONT=courier new]**xfce4-terminal**[/FONT][/COLOR].

my big interest is what backslash style or similar sequences can do.  and i don't mean a means so emulate having the proper keyboard by entering the character code and the terminal passing the raw code in the width (8 bit, 16 bit, 32 bit) that the terminal is emulating.  i mean sequences passed to applications as the characters actually typed where this can encode unicode when the sequences are, eventually, processed for the encoding.  i want to pass an encoded form like this when passing command arguments or piped input to a shell.

---

### Post by Impavidus on 2019-12-31
I'm not sure what you mean by "the unconverted ascii character, starting with the u in lower case". Also not sure what you mean by "the raw code in the width (8 bit, 16 bit, 32 bit) that the terminal is emulating". The ctrl+shift+u trick works in xfce4-terminal, in firefox, nearly everywhere.

If you want to pass the actual escape sequence to the application and have the application process it, just type an escape sequence, making sure it's not already processed by the shell, and making sure your application actually supports escape sequences. Many do, as it's a simple feature, but for example /bin/echo doesn't. The bash shell builtin echo does.

As a few examples, when I want my terminal to wish me a good day in greek, I can type:```
# By switching keyboard layout with the <menu> key:
# Actual keypresses:
# e c h o <space> <menu> shift+k a l h m ; e r a <menu> <enter>
# Gives this command line:
$ echo &#922;&#945;&#955;&#951;&#956;&#941;&#961;&#945;

# By having the terminal interpret escape sequences:
# Actual keypresses:
# e c h o <space> ctrl+shift+u 3 9 a <space> ctrl+shift+u 3 b 1 <space> ctrl+shift+u 3 b b <space> ctrl+shift+u 3 b 7 <space> ctrl+shift+u 3 b c <space> ctrl+shift+u 3 a d <space> ctrl+shift+u 3 c 1 <space> ctrl+shift+u 3 b 1 <space> <enter>
# Gives the command line:
$ echo &#922;&#945;&#955;&#951;&#956;&#941;&#961;&#945;

# By having bash interpret escape sequences:
# Just type this at the prompt:
$ echo $'\u39a\u3b1\u3bb\u3b7\u3bc\u3ad\u3c1\u3b1'
# Maybe that is what you mean?

# By having the application interpret the escape sequences. Use quotes to prevent the shell from processing the backslashes.
# Note that that doesn't really happen here, as echo is a shell builtin and the actual /bin/echo program
# doesn't handle escape sequences for multibyte characters.
# Type at the prompt:
$ echo -e '\u39a\u3b1\u3bb\u3b7\u3bc\u3ad\u3c1\u3b1'
```In all cases the characters I actually types are sent to the process interpreting the escape sequences, then they are converted to UTF-8. In Linux nearly all text is in UTF-8.

---

### Post by Skaperen on 2019-12-31
basically, it's not happening for me.  no conversion took place.  i just got to see the literal characters i typed.  while holding down shift and ctrl when i typed the "u", i saw a "u".  then i typed 0412. then Unicode number for Russian letter "&#1042;".  but i didn't get "&#1042;".  all i got was "u0412" ("u" was in lower case).

the bash interpreted backslash example worked.  i got "&#922;&#945;&#955;&#951;&#956;&#941;&#961;&#945;", though when googling that it seems google misunderstands the codes.  8 bytes in for 8 Greek letters, must be an ISO8859 coding.

---

### Post by Skaperen on 2019-12-31
[here]("http://ipal.net/unicode-utf8-all.xz") is my list of Unicode to UTF-8 mapping.  one of the many benefits of UTF-8 coding is that it sorts correctly. it's about 1.2 MB that uncompresses to about 36 MB.

---

### Post by Impavidus on 2020-01-01
I thought you didn't need anything special to enable the ctrl+shift+u input. I certainly didn't. When I hit ctrl+shift+u, I get an underlined u, then it shows the hexadecimal code as I type it, and when I terminate with space, the whole _u0412_ is converted into &#1042;. (BTW, no need to type the leading 0, but it does no harm).

When I use output redirect to echo &#922;&#945;&#955;&#951;&#956;&#941;&#961;&#945; to a file, I get 17 bytes (including a terminating newline). I think your web browser does an encoding conversion before sending things to google, or google does something weird.

BTW, terminology is a bit fuzzy here. What Unicode does it that it defines a mapping between character names and numbers, what UTF-8 does is that it defines a mapping between numbers and byte sequences. In principle, these don't have to be linked, but in practice, they are.

---

### Post by The Cog on 2020-01-01
I know it's not a lot of help, but I use Xubuntu, and the Ctrl-Shift-U input has worked for me for years (currently on 19.10). So I think there may be something unusual in your setup. I've not been able to find a setting anywhere that looks like a good suspect.
Just in case it provides a clue, the output of **locale** in a terminal for me is:
```
steve@StevesPC:~$ locale
LANG=en_GB.UTF-8
LANGUAGE=en_GB:en
LC_CTYPE="en_GB.UTF-8"
LC_NUMERIC=en_GB.UTF-8
LC_TIME=en_GB.UTF-8
LC_COLLATE="en_GB.UTF-8"
LC_MONETARY=en_GB.UTF-8
LC_MESSAGES="en_GB.UTF-8"
LC_PAPER=en_GB.UTF-8
LC_NAME=en_GB.UTF-8
LC_ADDRESS=en_GB.UTF-8
LC_TELEPHONE=en_GB.UTF-8
LC_MEASUREMENT=en_GB.UTF-8
LC_IDENTIFICATION=en_GB.UTF-8
LC_ALL=
```
and in Settings -> Language Support, my "Keyboard input method system" is "none".

---

### Post by Skaperen on 2020-01-01
i previously had used a keyboard input for 8-bit coding that did not show the number as it was typed.  it would feed the byte as input as soon as the 3 decimal digits were entered.  i was making the assumption that Ctrl+Shift+U worked the same way and jumped to the quick conclusion that feature was not active.  the one i used long ago was a loadable kernel module.  the kernel can do this before the echo happens and that is apparently what that module did.  as soon as i saw "u0412" i just backspaced.  had i gone ahead with another character, i would have seen the converted character.  this conversion does work in firefox.  so is it being done in the kernel (i'm guessing no, since it would not try to show the echo of the digits on the X display) or in X (probably not for similar reasons) or in the app (xfce4-terminal and firefox)?

the 8 bytes i was referring to was the 8 backslash octal codes.  i'm guessing something translated 8859 coding to Unicode which was then encoded as UTF-8.  BTW, i have written UTF-8 encoding and decoding software in both C and Python3; i do know what it is.  i was looking for types of coded data entry to check how some scripts i'm creating might need to deal with user input that it gets before any encoding happens.  i can enter such codes in Python3 string literals in source code.

---

### Post by Impavidus on 2020-01-02
As the codes have variable length, you need some kind of terminator. Apparently, this conversion of ctrl+shift+u codes is done in GTK. I guess Qt has its own methods of unicode input handling, but I don't have any Qt applications installed to test.

I've written some UTF-8 encoding, decoding and validating functions in C, but never in Python. As long as your input comes from a terminal, or a not-too-ancient text file created on a Linux system, or you use something like GTK, you can safely assume it's UTF-8 encoded Unicode, and as long as your output is to a terminal, to a text file, or something like GTK, you can safely output UTF-8 encoded Unicode. When you want to handle your own input method or text rendering or if you care about compatibility with old files in legacy 8-bit encodings (iso-8859-n etc.) or with Windows (where UTF-16 encoded Unicode seems to occur), you have to pay attention to the encoding used.

---

### Post by Skaperen on 2020-01-02
in Python, the way Unicode is handled in escape sequences is "\u0123" and "\U01234567" where the digits are always hexadecimal.  one way i thought of would be "\u" or "\U" to start  hexadecimal digits where any non-digit ends the sequence and "\ " ends it w/o being an added character (so "\u12345\ foo" has a length of 4 Unicode characters ... avoiding the "f" being interpreted as a digit).  if you really want a space before "foo" then do "\u12345 foo".

input as UTF-8 is usually a safe bet.  with ctrl+shift+u that should work for the entire Unicode code space.  but if this is done in GTK and Qt, it might not be universal enough to totally dismiss getting input with escape sequences.  then the issue is whether you want to support that in your app.  if we can get ctrl+shift+u in more places (X, Wayland, etc) this would be universal enough to deprecate all terminal input backslashes for anything but backslashes.

---

