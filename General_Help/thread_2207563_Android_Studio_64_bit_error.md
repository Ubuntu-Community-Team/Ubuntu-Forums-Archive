---
title: "Android Studio 64 bit error"
date: 2014-02-24
forum: General Help
---

### Post by kielyk on 2014-02-24
I have installed Android Studio on Ubuntu 14 64 bit. I am getting the following error and can't run anything on the AVD. I am only a light user so don't know a whole lot about linux. Any help would be much appreciated so thanks in advance.
Unclosed ': Unclosed '
java.lang.RuntimeException: Unclosed '
    at javax.swing.text.html.CSSParser.readTill(CSSParser.java:674)
    at javax.swing.text.html.CSSParser.nextToken(CSSParser.java:478)
    at javax.swing.text.html.CSSParser.parseIdentifiers(CSSParser.java:374)
    at javax.swing.text.html.CSSParser.parseDeclaration(CSSParser.java:357)
    at javax.swing.text.html.CSSParser.parseDeclarationBlock(CSSParser.java:325)
    at javax.swing.text.html.CSSParser.parseRuleSet(CSSParser.java:272)
    at javax.swing.text.html.CSSParser.getNextStatement(CSSParser.java:178)
    at javax.swing.text.html.CSSParser.parse(CSSParser.java:153)
    at javax.swing.text.html.StyleSheet$CssParser.parse(StyleSheet.java:3187)
    at javax.swing.text.html.StyleSheet.addRule(StyleSheet.java:307)
    at javax.swing.text.html.HTMLDocument$HTMLReader.addCSSRules(HTMLDocument.java:3807)
    at javax.swing.text.html.HTMLDocument$HTMLReader$HeadAction.end(HTMLDocument.java:2944)
    at javax.swing.text.html.HTMLDocument$HTMLReader.handleEndTag(HTMLDocument.java:2682)
    at javax.swing.text.html.parser.DocumentParser.handleEndTag(DocumentParser.java:240)
    at javax.swing.text.html.parser.Parser.parse(Parser.java:2263)
    at javax.swing.text.html.parser.DocumentParser.parse(DocumentParser.java:122)
    at javax.swing.text.html.parser.ParserDelegator.parse(ParserDelegator.java:101)
    at javax.swing.text.html.HTMLEditorKit.read(HTMLEditorKit.java:262)
    at javax.swing.JEditorPane.setText(JEditorPane.java:1415)
    at com.intellij.ide.IdeTooltipManager.initPane(IdeTooltipManager.java:578)
    at com.intellij.ide.IdeTooltipManager.initPane(IdeTooltipManager.java:495)
    at com.intellij.ui.popup.PopupFactoryImpl.createHtmlTextBalloonBuilder(PopupFactoryImpl.java:1033)
    at com.intellij.openapi.wm.impl.ToolWindowManagerImpl.notifyByBalloon(ToolWindowManagerImpl.java:1414)
    at com.intellij.execution.runners.ExecutionUtil$2.run(ExecutionUtil.java:104)
    at com.intellij.util.ui.UIUtil.invokeLaterIfNeeded(UIUtil.java:1999)
    at com.intellij.execution.runners.ExecutionUtil.handleExecutionError(ExecutionUtil.java:101)
    at com.intellij.execution.ProgramRunnerUtil.executeConfiguration(ProgramRunnerUtil.java:145)
    at com.intellij.execution.impl.ExecutionManagerImpl.start(ExecutionManagerImpl.java:367)
    at com.intellij.execution.impl.ExecutionManagerImpl.access$400(ExecutionManagerImpl.java:58)
    at com.intellij.execution.impl.ExecutionManagerImpl$4.run(ExecutionManagerImpl.java:349)
    at com.intellij.util.concurrency.QueueProcessor.runSafely(QueueProcessor.java:238)
    at com.intellij.util.Alarm$Request$1.run(Alarm.java:297)
    at com.intellij.openapi.application.impl.LaterInvocator$FlushQueue.run(LaterInvocator.java:346)
    at java.awt.event.InvocationEvent.dispatch(InvocationEvent.java:251)
    at java.awt.EventQueue.dispatchEventImpl(EventQueue.java:733)
    at java.awt.EventQueue.access$200(EventQueue.java:103)
    at java.awt.EventQueue$3.run(EventQueue.java:694)
    at java.awt.EventQueue$3.run(EventQueue.java:692)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.security.ProtectionDomain$1.doIntersectionPrivilege(ProtectionDomain.java:76)
    at java.awt.EventQueue.dispatchEvent(EventQueue.java:703)
    at com.intellij.ide.IdeEventQueue.defaultDispatchEvent(IdeEventQueue.java:697)
    at com.intellij.ide.IdeEventQueue._dispatchEvent(IdeEventQueue.java:524)
    at com.intellij.ide.IdeEventQueue.dispatchEvent(IdeEventQueue.java:335)
    at java.awt.EventDispatchThread.pumpOneEventForFilters(EventDispatchThread.java:242)
    at java.awt.EventDispatchThread.pumpEventsForFilter(EventDispatchThread.java:161)
    at java.awt.EventDispatchThread.pumpEventsForHierarchy(EventDispatchThread.java:150)
    at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:146)
    at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:138)
    at java.awt.EventDispatchThread.run(EventDispatchThread.java:91)

---

