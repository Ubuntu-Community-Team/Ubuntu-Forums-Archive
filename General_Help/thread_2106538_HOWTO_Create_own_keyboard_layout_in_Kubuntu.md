---
title: "HOWTO: Create own keyboard layout in Kubuntu"
date: 2013-01-19
forum: General Help
---

### Post by newHippie on 2013-01-19
Hi, I'm new here. Normally I write in the German Ubuntu forum but I thought that a HowTo has to be in English to rich more people so I have registered me here.

I found it really complicated to define a new layout in Kubuntu so I decided to write a short HowTo for all of you, who have the idea of making own keyboard layouts. It is my first tutorial so every comments and corrections are welcome.
 

 
1. Download &#8220;**Keyboardlayouteditor**&#8221;     from [http://code.google.com/p/keyboardlayouteditor/](http://code.google.com/p/keyboardlayouteditor/) and install     **Character Map** (can be found in the repositories). Read the README     file of  Keyboardlayouteditor to make it work.
2. Start the Keyboardlayouteditor and     define the root path to **[FONT=Courier New]/usr/share/X11/xkb/[/FONT] **otherwise the layouts     will not load.
3. Load the layout you want to change     from **/usr/share/X11/xkb/symbols**.
4. Start Character Map (for me the     program does not start when push the button in Keyboardlayouteditor).
5. Drag and drop symbols and create     your layout.
6. Save the layout. The names and     layout details are not important, because we will change them in the     text file later.
7. Open the saved file and the     original layout file from **/usr/share/X11/xkb/symbols** you have     changed in a text editor. Be sure to make a backup of the original     file.
8. Copy the whole text form your own     layout to the end of the original file.
9. Change the **xkb_symbols** variable to     a good name without spaces.
10. Change the Description as you     want. I have not found out where you see this description later.
11. To make sure you are in the right     file control whether the included layout for you changed layout is     in the same file.
12. Save the edited file under the     same name.
13. Open the files     **/usr/share/X11/xkb/rules/base.xml** and **    /usr/share/X11/xkb/rules/evdev.xml**  with a text editor. Make sure to     make copies of the originals. You do not need to change **xfree86.xml**     because it is a link to **base.xml**.
14. Search for the language for which     you want add a new layout variant.
15. Make sure the     **<shortDescription>XXX</shortDescription>** have the same **    XXX** as you previously changed and saved layout file. For example     &#8220;en&#8221; or &#8220;de&#8221;.
16. Go to the end of the definition     and put the following text in both files

```

     &#8230;  
     </variant>
    ------------------ new text ----------------------
     <variant>
     <configItem>
         <name>[COLOR=Red]**XXX**[/COLOR]</name>
         <description>[COLOR=Red]**YYY**[/COLOR]</description>
         <languageList>
         <iso639Id>[COLOR=Red]**ZZZ**[/COLOR]</iso639Id>
         </languageList>
     </configItem>
     </variant>
     ----------------- end of the new text -----------
     </variantList>
     &#8230; 

```    Where **XXX** is you** xkb_symbols **name, **YYY** a description and the **ZZZ** a language abbreviation.
 
17. Save the files and reboot.
18. Now you should be able to find     your layout as a variant of the chosen language.
19. I have noticed, that when you want     make some changes afterwards you have to change the **xkb_symbols**     variable in the layout file and in both .xml file to make the     changes work. Not sure but it can even be, that the new **xkb_symbols**     variable must be really a new one and not just changed to the older     one. I think it is because once compiled the layouts do not change     when nothing &#8220;new&#8221; in the .xml files happens.
20. Have fun.

---

