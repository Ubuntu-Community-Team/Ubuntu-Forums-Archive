---
title: "Cannot apply styles in Open Office Impress (presentation)"
date: 2008-06-10
forum: General Help
---

### Post by TheodoreWard on 2008-06-10
I have always had this problem and have had little luck finding help, so I would assume it is me, but I have tried everything I can think of.

The problem: In Impress I want to define a style to apply to code snippets so I don't have to manually format everthing everytime I put some code into a slide.

I press F11 and bring up style manager, format the text, create a new style from it.

Then if I ever try to select anything else and apply my new style, it does absolutely nothing. I have tried selecting the text and double clicking, using the format painter, everything I can think of and it makes no difference.

Anyone else have this problem?

---

### Post by Brucevdk on 2008-06-15
I thought I'd look into this and I have been scarred for life, what a horrible experience. After some 15 minutes and reading bits here and there from several manuals I think I've finally managed to somewhat figure out how the styles work in OpenOffice.org Impress.

From [The OpenOffice Impress User Guide, chapter Working with styles](http://www.linuxtopia.org/online_books/office_guides/openoffice_impress_guide/openoffice_impress_Working_with_styles.html) (also see [What are styles? Why use them? from the OOoAuthors User Manual](http://wiki.services.openoffice.org/wiki/Documentation/OOoAuthors_User_Manual/Impress_Guide/What_are_styles%3F_Why_use_them%3F):
> 
If you are familiar with styles in Writer, you will find both similarities and differences in Impress. The presentation styles are similar to paragraph styles in Writer and are used in a very similar fashion. You cannot create new presentation styles but you can fully configure the existing ones. [...] In Impress you will also find the graphic styles very useful. As the name suggests, graphic styles define the characteristics of a graphic object (including a text object).


Note that next to not being able to create new presentation styles, you also cannot really *apply* them as you'd do in Writer. For example, you cannot change something Impress has determined to be a subtitle to a title. From what I gather this is what you seem to be trying to do. 

The only thing you can really do is create custom text boxes, to which graphic styles can be applied. See:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=74112&stc=1&d=1213528118[/IMG]

[SIZE="4"]Under the hood[/SIZE]
You can ignore this if you're not interested, and skip to the summary. So how does this actually look like "under the hood" (in this case referring to the underlying format)? Well the only difference really is that instead of using the attribute *draw:style-name* presentation shapes use *presentation:style-name* in combination with *presentation:class*. [The OpenDocument (version 1.1) specification](http://www.oasis-open.org/committees/tc_home.php?wg_abbrev=office) states:

> 
The draw:style-name and presentation:style-name attributes specify a style for the drawing shape. If draw:style-name is used, the shape is a regular graphic shape. If presentation:style-name is used, the shape is a presentation shape as described in section 9.6.


Section 9.6. states the following:
> 
Presentation shapes are special text box, image, object or thumbnail drawing shapes contained in a presentation. Presentation shapes use styles with a style family value of presentation, unlike drawing shapes which use styles with a style family value of graphic. Presentation shapes can be empty, acting only as placeholders. If a draw page's presentation layout (see section 14.15) is changed, all presentation shapes are adapted automatically.

Standard drawing shapes can also be used in presentations. The presentation:class attribute distinguishes presentation shapes from drawing shapes. Unlike presentation shapes, standard drawing shapes are not adapted if the presentation page layout is changed.


[SIZE="4"]Summary[/SIZE]
So summarizing.
[LIST]
[*]You can't create any new presentation styles.
[*]You can't really change the presentation style anyways.
[*]You can't apply graphics styles to presentation shapes.
[*]Presentation shapes in Impress will stay presentation shapes forever.
[*]OpenOffice.org Impress is known to cause seizures.
[/LIST]

---

### Post by TheodoreWard on 2008-06-18
Wow, well thanks a ton for all the research. I was getting the impression it was something like what you mention as it seemed if Impress thought something was a title or whatever, that's what it kept on being.

I appreciate the confirmation so at least I know its not just me. I am surprised I haven't seen more posts on this topic though.

Ted

---

### Post by moritz-s on 2008-07-05
This just about drove me insane. I've got a large-ish presentation, and I need to change the style of mathematical symbols, variables, etc in all of it. It's sans, bold now, and needs to be serif, italic. "Okay, this will be somewhat tedious, maybe I should have used tex after all, " I thought, "but it'll be all right, I'll use styles." Turns out you can't, nice research by the way, too bad I only found this thread after 15 minutes of painful trial-and-error (mostly error).

Then I figure there has got to be some way to copy/paste the formatting of text. And there is! The format painter does exactly what I need. I discover it while looking through the commands in the customize dialogue, and set a shortcut to it. However, using the shortcut does nothing - why?! I google it and discover there's actually a prominent toolbar button which I had never noticed -- and it's gray. WTF? Apparently this only works in Writer. In Impress it's eternally disabled for no apparent reason. Great!

At this point I'm really annoyed. My next idea involves 1) make the change once, 2) copy the changed text, 3) paste it at the next occurence, 4) retype the occurence, in the style of the text I just pasted. Talk about tedium! But at first, this doesn't work either: When I paste the text, the font gets changed! It stays italic, though. I restart OO, and now it works as intended. But it turns out it's way too much work, it's worse than selecting the right font and formatting, if only a little worse...

So finally, I get the idea to create a macro. I've never done an OO macro, but I program for a living, so I figure it can't be too difficult. After a very brief look at the macro editor which has nothing like completion which would make a discovering a completely unknown language feasible, I change my mind. "But," I think, "there must be a macro recorder." And there is! But it's grayed out in Impress. I blankly stare at the screen for about three minutes, then I open Writer where obviously the recorder is enabled, run through the paces of the format change and save the macro as expletiveOO. I edit the generated macro to do some fine tuning -- incidently, there's no way I could have written that myself (*dispatcher.executeDispatch(document, ".uno:CharFontName", "", 0, args1())*... I was figuring more something along the lines of selection.setFont(...)).

Finally, I set up a shortcut to the macro, and now I'm flying through the changes. Even with the setup time, it'll be faster than doing each change manually.

---

### Post by Brucevdk on 2008-07-05
Thanks for sharing ;-)

> **moritz-s said:**
> I edit the generated macro to do some fine tuning -- incidently, there's no way I could have written that myself (*dispatcher.executeDispatch(document, ".uno:CharFontName", "", 0, args1())*... I was figuring more something along the lines of selection.setFont(...)).

Mathias Bauer, Project Lead OpenOffice.org Writer, discusses this on the on the OpenOffice.org Development mailing list ([see this thread](http://www.mail-archive.com/dev@openoffice.org/msg07527.html)). Note the following statement:

[QUOTE=Mathias Bauer]But this simple recorder still isn't the "real" recorder that developers and development newbies want, they want a tool that teaches them the "real" OOo API (not the Dispatch API), not a simple automation tool.[/QUOTE]

The reason why the macro recorder is grayed out in Impress is also discussed in the linked thread. 

[QUOTE=Mathias Bauer]Because it is not implemented. The macro recorder builds upon some
functionality of the old sfx2 framework. This part was never implemented reliably in Draw/Impress and the residues have been removed after we moved to the new UNO based API. Writer and Calc where a bit more lazy removing that parts and so it was possible to use it again.
[/QUOTE]

---

