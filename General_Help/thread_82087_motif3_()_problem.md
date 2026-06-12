---
title: "motif3 (?) problem"
date: 2005-10-25
forum: General Help
---

### Post by wgscott on 2005-10-25
I have a piece of proprietary software that depends upon motif.  After the ubuntu upgrade, upon startup of this program, I get errors of the form pasted in below.

Presumably, as a consequence, the windows don't take keyboard input.

I've tried lesstiff and libmotif but I get the same problems.


```

Warning: translation table syntax error: Unknown keysym name:  osfActivate
Warning: ... found while parsing ':<Key>osfActivate:            ManagerParentActivate()'
Warning: String to TranslationTable conversion encountered errors
Warning: translation table syntax error: Unknown keysym name:  osfBeginLine
Warning: ... found while parsing ':<Key>osfBeginLine:           ManagerGadgetTraverseHome()'
Warning: String to TranslationTable conversion encountered errors
Warning: translation table syntax error: Unknown keysym name:  osfActivate
Warning: ... found while parsing ':<Key>osfActivate:    ManagerParentActivate()'
Warning: String to TranslationTable conversion encountered errors
Warning: translation table syntax error: Unknown keysym name:  osfHelp
Warning: ... found while parsing ':<Key>osfHelp:                        ManagerGadgetHelp()'
Warning: String to TranslationTable conversion encountered errors
Warning: translation table syntax error: Unknown keysym name:  osfUp
Warning: ... found while parsing ':<Key>osfUp:          SelectionBoxUpOrDown(0)'
Warning: String to AcceleratorTable conversion encountered errors
Warning: translation table syntax error: Unknown keysym name:  osfActivate
Warning: ... found while parsing ':<Key>osfActivate:    PrimitiveParentActivate()'
Warning: String to TranslationTable conversion encountered errors
Warning: translation table syntax error: Unknown keysym name:  osfHelp
Warning: ... found while parsing ':<Key>osfHelp:                Help()'
Warning: String to TranslationTable conversion encountered errors
Warning: translation table syntax error: Unknown keysym name:  osfActivate
Warning: ... found while parsing ':<Key>osfActivate:    PrimitiveParentActivate()'
Warning: String to TranslationTable conversion encountered errors
Warning: translation table syntax error: Unknown keysym name:  osfCancel
Warning: ... found while parsing ':<Key>osfCancel:      MenuEscape()'
Warning: String to TranslationTable conversion encountered errors
Warning: translation table syntax error: Unknown keysym name:  osfSelect
Warning: ... found while parsing ':<Key>osfSelect:      ArmAndActivate()'
Warning: String to TranslationTable conversion encountered errors
Warning: translation table syntax error: Unknown keysym name:  osfActivate
Warning: ... found while parsing ':<Key>osfActivate:            PrimitiveParentActivate()'
Warning: String to TranslationTable conversion encountered errors
Warning: translation table syntax error: Unknown keysym name:  osfPrimaryPaste
Warning: ... found while parsing ':m <Key>osfPrimaryPaste:cut-primary()'
Warning: String to TranslationTable conversion encountered errors
Warning: translation table syntax error: Unknown keysym name:  osfSelect
Warning: ... found while parsing ':<Key>osfSelect:      ManagerGadgetSelect()'
Warning: String to TranslationTable conversion encountered errors
Warning: translation table syntax error: Unknown keysym name:  osfSelect
Warning: ... found while parsing ':<Key>osfSelect:      MenuBarGadgetSelect()'
Warning: String to TranslationTable conversion encountered errors
Warning: translation table syntax error: Unknown keysym name:  osfActivate
Warning: ... found while parsing ':<Key>osfActivate:    ManagerParentActivate()'
Warning: String to TranslationTable conversion encountered errors
Warning: translation table syntax error: Unknown keysym name:  osfHelp
Warning: ... found while parsing ':<Key>osfHelp:                MenuHelp()'
Warning: String to TranslationTable conversion encountered errors
Warning: translation table syntax error: Unknown keysym name:  osfSelect
Warning: ... found while parsing ':<Key>osfSelect:      KeySelect()'
Warning: String to TranslationTable conversion encountered errors
Warning: translation table syntax error: Unknown keysym name:  osfSelect
Warning: ... found while parsing ':<Key>osfSelect:      KeySelect()'
Warning: String to TranslationTable conversion encountered errors
Warning: translation table syntax error: Unknown keysym name:  osfActivate
Warning: ... found while parsing ':<Key>osfActivate:    PrimitiveParentActivate()'
Warning: String to TranslationTable conversion encountered errors
Warning: translation table syntax error: Unknown keysym name:  osfSelect
Warning: ... found while parsing ':<Key>osfSelect:      ArmAndActivate()'
Warning: String to TranslationTable conversion encountered errors
Warning: translation table syntax error: Unknown keysym name:  osfActivate
Warning: ... found while parsing ':<Key>osfActivate:    DrawingAreaInput() ManagerParentActivate()'
Warning: String to TranslationTable conversion encountered errors
Warning: translation table syntax error: Unknown keysym name:  osfUp
Warning: ... found while parsing ':<Key>osfUp:          DrawingAreaInput() ManagerGadgetTraverseUp()'
Warning: String to TranslationTable conversion encountered errors
Warning: translation table syntax error: Unknown keysym name:  osfPrimaryPaste
Warning: ... found while parsing ':m <Key>osfPrimaryPaste:cut-primary()'
Warning: String to TranslationTable conversion encountered errors
Warning: Locale not supported for XmbTextListToTextProperty
Warning: Cannot convert XmString to compound text
Warning: translation table syntax error: Unknown keysym name:  osfBeginLine
Warning: ... found while parsing ':s c <Key>osfBeginLine:               ListBeginDataExtend()'
Warning: String to TranslationTable conversion encountered errors
Warning: translation table syntax error: Unknown keysym name:  osfActivate
Warning: ... found while parsing ':<Key>osfActivate:            PrimitiveParentActivate()'
Warning: String to TranslationTable conversion encountered errors
Warning: Locale not supported for XmbTextListToTextProperty
Warning: Cannot convert XmString to compound text
Warning: translation table syntax error: Unknown keysym name:  osfCancel
Warning: ... found while parsing '<Key>osfCancel:                       MenuEscape()'
Warning: String to TranslationTable conversion encountered errors
Warning: translation table syntax error: Unknown keysym name:  osfActivate
Warning: ... found while parsing ':<Key>osfActivate:            PrimitiveParentActivate()'
Warning: String to TranslationTable conversion encountered errors
Warning: Locale not supported for XmbTextListToTextProperty
Warning: Cannot convert XmString to compound text
Warning: Locale not supported for XmbTextListToTextProperty
Warning: Cannot convert XmString to compound text
Warning: Locale not supported for XmbTextListToTextProperty
Warning: Cannot convert XmString to compound text
Warning: Locale not supported for XmbTextListToTextProperty
Warning: Cannot convert XmString to compound text
Warning: Locale not supported for XmbTextListToTextProperty
Warning: Cannot convert XmString to compound text
Warning: Locale not supported for XmbTextListToTextProperty
Warning: Cannot convert XmString to compound text
Warning: Locale not supported for XmbTextListToTextProperty
Warning: Cannot convert XmString to compound text
Warning: Locale not supported for XmbTextListToTextProperty
Warning: Cannot convert XmString to compound text
Warning: translation table syntax error: Unknown keysym name:  osfActivate
Warning: ... found while parsing ':<Key>osfActivate:            PrimitiveParentActivate()'
Warning: String to TranslationTable conversion encountered errors
Warning: Locale not supported for XmbTextListToTextProperty
Warning: Cannot convert XmString to compound text

```

---

### Post by wgscott on 2005-10-25
The answer is:

export XKEYSYMDB=/usr/share/X11/XKeysymDB


This is also needed to get the grace package to work right on Breezy, BTW.

---

