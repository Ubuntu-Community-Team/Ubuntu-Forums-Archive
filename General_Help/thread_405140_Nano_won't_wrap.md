---
title: "Nano won't wrap"
date: 2007-04-09
forum: General Help
---

### Post by Mateo on 2007-04-09
for some reason nano isn't wrapping my text on long lines.  I have tried using the Alt+L, which is supposed to toggle wrapping but it's not working.  any ideas what can be going on here?  by the way, using nano 2.0.2

---

### Post by Mateo on 2007-04-09
bump, here's my .nanorc file.  Could this be a feisty bug?

```
## Sample initialization file for GNU nano.
##
## Please note that you must have configured nano with --enable-nanorc
## for this file to be read!  Also note that this file should not be in
## DOS or Mac format, and that characters specially interpreted by the
## shell should not be escaped here.
##
## To make sure a value is disabled, use "unset <option>".
##
## For the options that take parameters, the default value is given.
## Other options are unset by default.
##
## Quotes inside string parameters don't have to be escaped with
## backslashes.  The last double quote in the string will be treated as
## its end.  For example, for the "brackets" option, ""')>]}" will match
## ", ', ), >, ], and }.

## Use auto-indentation.
# set autoindent

## Backup files to filename~.
# set backup

## The directory to put unique backup files in.
# set backupdir ""

## Do backwards searches by default.
# set backwards

## Use bold text instead of reverse video text.
# set boldtext

## The characters treated as closing brackets when justifying
## paragraphs.  They cannot contain blank characters.  Only closing
## punctuation, optionally followed by closing brackets, can end
## sentences.
##
# set brackets ""')>]}"

## Do case sensitive searches by default.
# set casesensitive

## Constantly display the cursor position in the statusbar.  Note that
## this overrides "quickblank".
# set const

## Use cut to end of line by default.
# set cut

## Set the line length for wrapping text and justifying paragraphs.
## If fill is 0 or less, the line length will be the screen width less
## this number.
##
# set fill -8

## Enable ~/.nano_history for saving and reading search/replace strings.
set historylog

## The opening and closing brackets that can be found by bracket
## searches.  They cannot contain blank characters.  The former set must
## come before the latter set, and both must be in the same order.
##
# set matchbrackets "(<[{)>]}"

## Use the blank line below the titlebar as extra editing space.
# set morespace

## Enable mouse support, if available for your system.  When enabled,
## mouse clicks can be used to place the cursor, set the mark (with a
## double click), and execute shortcuts.  The mouse will work in the X
## Window System, and on the console when gpm is running.
##
# set mouse

## Allow multiple file buffers (inserting a file will put it into a
## separate buffer).  You must have configured with --enable-multibuffer
## for this to work.
##
# set multibuffer

## Don't convert files from DOS/Mac format.
# set noconvert

## Don't follow symlinks when writing files.
# set nofollow

## Don't display the helpful shortcut lists at the bottom of the screen.
# set nohelp

## Don't add newlines to the ends of files.
# set nonewlines

## Don't wrap text at all.
# set nowrap

## Set operating directory.  nano will not read or write files outside
## this directory and its subdirectories.  Also, the current directory
## is changed to here, so any files are inserted from this dir.  A blank
## string means the operating directory feature is turned off.
##
# set operatingdir ""

## Preserve the XON and XOFF keys (^Q and ^S).
# set preserve

## The characters treated as closing punctuation when justifying
## paragraphs.  They cannot contain blank characters.  Only closing
## punctuation, optionally followed by closing brackets, can end
## sentences.
##
# set punct "!.?"

## Do quick statusbar blanking.  Statusbar messages will disappear after
## 1 keystroke instead of 26.  Note that "const" overrides this.
##
# set quickblank

## The email-quote string, used to justify email-quoted paragraphs.
## This is an extended regular expression if your system supports them,
## otherwise a literal string.  Default:
# set quotestr "^([ 	]*[#:>\|}])+"
## if you have extended regular expression support, otherwise:
# set quotestr "> "

## Fix Backspace/Delete confusion problem.
# set rebinddelete

## Fix numeric keypad key confusion problem.
# set rebindkeypad

## Do extended regular expression searches by default.
# set regexp

## Make the Home key smarter.  When Home is pressed anywhere but at the
## very beginning of non-whitespace characters on a line, the cursor
## will jump to that beginning (either forwards or backwards).  If the
## cursor is already at that position, it will jump to the true
## beginning of the line.
# set smarthome

## Use smooth scrolling as the default.
set smooth

## Use this spelling checker instead of the internal one.  This option
## does not properly have a default value.
##
# set speller "aspell -x -c"

## Allow nano to be suspended.
set suspend

## Use this tab size instead of the default; it must be greater than 0.
# set tabsize 8

## Convert typed tabs to spaces.
# set tabstospaces

## Save automatically on exit, don't prompt.
# set tempfile

## Disallow file modification.  Why would you want this in an rcfile? ;)
# set view

## The two single-column characters used to display the first characters
## of tabs and spaces.  187 in ISO 8859-1 (0000BB in Unicode) and 183 in
## ISO-8859-1 (0000B7 in Unicode) seem to be good values for these.
# set whitespace "  "

## Detect word boundaries more accurately by treating punctuation
## characters as parts of words.
# set wordbounds


## Color setup
##
## Format:
##
## syntax "short description" ["filename regex" ...]
##
## The "none" syntax is reserved; specifying it on the command line is
## the same as not having a syntax at all.  The "default" syntax is
## special: it takes no filename regexes, and applies to files that
## don't match any other syntax's filename regexes.
##
## color foreground,background "regex" ["regex"...]
## or
## icolor foreground,background "regex" ["regex"...]
##
## "color" will do case sensitive matches, while "icolor" will do case
## insensitive matches.
##
## Valid colors: white, black, red, blue, green, yellow, magenta, cyan.
## For foreground colors, you may use the prefix "bright" to get a
## stronger highlight.
##
## To use multi-line regexes, use the start="regex" end="regex"
## [start="regex" end="regex"...] format.
##
## If your system supports transparency, not specifying a background
## color will use a transparent color.  If you don't want this, be sure
## to set the background color to black or white.
##
## If you wish, you may put your syntaxes in separate files.  You can
## make use of such files (which can only include "syntax", "color", and
## "icolor" commands) as follows:
##
## include "/path/to/syntax_file.nanorc"
##
## Unless otherwise noted, the name of the syntax file (without the
## ".nanorc" extension) should be the same as the "short description"
## name inside that file.  These names are kept fairly short to make
## them easier to remember and faster to type using nano's -Y option.
##
## All regexes should be extended regular expressions.


## Nanorc files
# include "/usr/share/nano/nanorc.nanorc"

## C/C++
# include "/usr/share/nano/c.nanorc"

## HTML
# include "/usr/share/nano/html.nanorc"

## TeX
include "/usr/share/nano/tex.nanorc"

## Quoted emails (under e.g. mutt)
# include "/usr/share/nano/mutt.nanorc"

## Patch files
# include "/usr/share/nano/patch.nanorc"

## Manpages
# include "/usr/share/nano/man.nanorc"

## Groff
# include "/usr/share/nano/groff.nanorc"

## Perl
# include "/usr/share/nano/perl.nanorc"

## Python
# include "/usr/share/nano/python.nanorc"

## Ruby
# include "/usr/share/nano/ruby.nanorc"

## Java
# include "/usr/share/nano/java.nanorc"

## Assembler
# include "/usr/share/nano/asm.nanorc"

## Bourne shell scripts
# include "/usr/share/nano/sh.nanorc"

## POV-Ray
# include "/usr/share/nano/pov.nanorc"
```

---

### Post by altaaa on 2007-04-09
I don't even have a .nanorc file; but maybe it's in this setting:

```
## Set the line length for wrapping text and justifying paragraphs.
## If fill is 0 or less, the line length will be the screen width less
## this number.
##
# set fill -8
```

You have it commented out.

---

### Post by Mateo on 2007-04-09
i've tried changing that, but it doesn't make a difference.

is it possible the files i'm using are not properly encoded or something?  how can i check that?

---

### Post by altaaa on 2007-04-09
I would try renaming your .nanorc to something like .nanorc.backup just to see how Nano reacts to that; see if pico gives you the same result. You can use the file command to view information about a file, try ```
file -i filename
```. I'm not sure how you can determine the encoding of a file though.

---

### Post by Mateo on 2007-04-09
here's the output, i'm assuming this is file.

```
chapter1.tex: text/plain; charset=utf-8
```

i've tried without the .nanorc.  tried typing pico instead. I see no difference.  I don't see how this is anything other than a bug.

---

### Post by altaaa on 2007-04-09
So the file -i does display the encoding. Cool, wasn't sure about that.

If I run nano without any arguments, it wraps the lines as it should.

If I run nano -w filename, the lines don't get wrapped.

But if I open a file with a non-wrapped line, it stays non-wrapped, although any new line I type will get wrapped :confused: 

Strange.

I know you probably don't want to hear this, but if I open the file in vi everything goes as expected ;)

---

### Post by Mateo on 2007-04-09
vi is too hard for me.  i can't even figure out how to exit it.  i'd rather get nano fixed.

---

### Post by altaaa on 2007-04-09
If you run nano with specific wrapping settings on a new file, does it wrap?

ie. nano -r -8 newfile

---

### Post by Mateo on 2007-04-09
yes, it does wrap that way.

---

### Post by altaaa on 2007-04-09
The -8 option should be the default option. I don't know why Nano doesn't wrap lines that are already in a file though.

It almost seems as this behavior is by design. At least I can't find any information on internet. Using ALT+L I can switch between line wrapping enabled/disabled, but Nano doesn't rearrange the non-wrapped lines.

Sorry, can't help you here...

---

### Post by Mateo on 2007-04-09
i can't change it with Alt+L.  I filed a bug report.  10 to 1 says it doesn't even get a reply.

---

