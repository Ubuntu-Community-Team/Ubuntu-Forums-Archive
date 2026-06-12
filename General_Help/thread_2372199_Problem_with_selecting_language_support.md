---
title: "Problem with selecting language support"
date: 2017-09-22
forum: General Help
---

### Post by James Wilde on 2017-09-22
I'm using Ubuntu-Mate 16.04.  English is my mother tongue but I live in Sweden so I want both languages supported.  I've moved American English down below the English line and British English above.  Now I want to add Swedish above the line, as I use Swedish formats for numbers, dates, etc.  If I move Swedish above the English line, it also lands above the British English line, and next time I log in all my menus are in Swedish.  If I try to move British English above the Swedish line, Swedish disappears to the bottom of the list, under the English line.

What I want is British English as the language of my menus, then Swedish as the language of my number formats and everything else can be ignored.  How do I get that?  I want the list to look like this:

British English
Swedish
English
masses of other forms of English

---

### Post by untrustytahr on 2017-09-22
So I am not multilingual and never had a need to understand system locales, but if you click the "Help" button on the Language Support GUI, you will see that someone has taken the time to create a help page for it.  One of the choices is "Advanced format settings".


> Advanced format settings


The Language Support method for setting regional formats assumes that one language-country combination (locale) is sufficient to set all the format aspects in accordance with your preferences. Even if that is often the case, situations when you want more fine tuned format settings may occur. For such a case, below are some variables that you may want to assign locale names individually. You can do so by editing the .profile configuration file in your home folder.


LC_NUMERIC
How you format your numbers. For example, in many countries a point is used as a decimal separator, while others use a comma.


LC_TIME
How your time and date are formatted.


LC_MONETARY
What currency you use, its name, and its symbol.


[SIZE=2]**[Click here]("https://help.ubuntu.com/community/Locale")**[/SIZE] for more LC_* variables with explanations.


An example
Take a user in the US who choose “English (United States)” in the drop-down list on the Regional Formats tab. If s/he prefers that dates and times are displayed more like what ISO 8601 prescribes than what's typically the case in the US, the below line may be added to the .profile file:


export LC_TIME="en_DK.UTF-8"


If you click the link inside that explanation, it will take you to a web page listing the variables that you can set and how to set them individually if desired.

---

### Post by James Wilde on 2017-09-25
Thanks, Untrustytahr.  That's just what I need.

---

