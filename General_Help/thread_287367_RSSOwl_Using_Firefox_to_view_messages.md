---
title: "RSSOwl Using Firefox to view messages"
date: 2006-10-28
forum: General Help
---

### Post by tenjin on 2006-10-28
Hi,

I just installed RSSOwl by following the instructions at [http://ubuntuguide.org/wiki/Ubuntu:Edgy/AddOnApplications](http://ubuntuguide.org/wiki/Ubuntu:Edgy/AddOnApplications)

Whenever I click on a message the applications bombs with the following message:

==================
Exception in thread "main" org.eclipse.swt.SWTError: XPCOM error -2147467262
        at org.eclipse.swt.browser.Browser.error(Browser.java:983)
        at org.eclipse.swt.browser.Browser.setText(Browser.java:1443)
        at net.sourceforge.rssowl.controller.panel.BrowserPanel.setText(Unknown Source)
        at net.sourceforge.rssowl.controller.panel.BrowserPanel.displayNews(Unknown Source)
        at net.sourceforge.rssowl.controller.NewsText.displayNewsInBrowser(Unknown Source)
        at net.sourceforge.rssowl.controller.NewsText.displayNews(Unknown Source)
        at net.sourceforge.rssowl.controller.NewsText.displayNews(Unknown Source)
        at net.sourceforge.rssowl.controller.NewsTable.onMouseDown(Unknown Source)
        at net.sourceforge.rssowl.controller.NewsTable$2.handleEvent(Unknown Source)
        at org.eclipse.swt.widgets.EventTable.sendEvent(EventTable.java:66)
        at org.eclipse.swt.widgets.Widget.sendEvent(Widget.java:1021)
        at org.eclipse.swt.widgets.Display.runDeferredEvents(Display.java:2867)
        at org.eclipse.swt.widgets.Display.readAndDispatch(Display.java:2572)
        at net.sourceforge.rssowl.controller.GUI.runEventLoop(Unknown Source)
        at net.sourceforge.rssowl.controller.GUI.showGui(Unknown Source)
        at net.sourceforge.rssowl.controller.RSSOwlLoader.<init>(Unknown Source)
        at net.sourceforge.rssowl.controller.RSSOwlLoader.main(Unknown Source)
==================

This is the contents of the file I use to run RSSOwl:

export MOZILLA_FIVE_HOME=/usr/lib/firefox
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:${MOZILLA_FIVE_HOME}:${LD_LIBRARY_PATH}
cd /opt/rssowl_linux_1_1_3_bin/
./run.sh


Can anyone suggest anything?

Cheers

D.

---

