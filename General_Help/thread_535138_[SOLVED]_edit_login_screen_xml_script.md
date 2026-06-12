---
title: "[SOLVED] edit login screen xml script"
date: 2007-08-26
forum: General Help
---

### Post by mitchi on 2007-08-26
I am using Ubuntu 7.04 and I'm trying to customize my login screen. I found out that editing the .xml file of the login theme can be done so I can apply my desired style. However, I cannot understand parts of the script, this is the script for the happygnome-list login theme:

<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE greeter SYSTEM "greeter.dtd">
<greeter>
  <item type="svg">
    <normal file="background.svg"/>
    <pos x="0" y="0" width="100%" height="-75"/>
  </item>
  <item type="rect">
    <normal color="#000000"/>
    <pos x="0" y="-75" width="100%" height="75"/>
    <fixed>
      <item type="rect">
        <normal color="#ffffff"/>
        <pos x="0" y="4" width="100%" height="100%"/>
        <box orientation="horizontal" spacing="10" xpadding="10" ypadding="10">
          <item type="button" id="options_button">
            <pos width="100" height="50" />
            <stock type="options"/>
          </item>
          <item type="list" id="language" combo="true">
            <pos  x="25" y="5" height="40" width="300"/>
          </item>
          <item type="list" id="session" combo="true">
            <pos x="50" y="5" height="40" width="300"/>
          </item>
        </box>
      </item>
    </fixed>
  </item>
  <item type="svg">
    <normal file="gnome-logo.svg"/>
    <pos x="-12" y="-12" width="30" height="47" anchor="se" />
  </item>
  <item type="label" id="clock">
    <normal color="#000000" font="Sans 12"/>
    <pos x="-80" y="-37" anchor="e"/>
    <text>%c</text>
  </item>

  <item type="rect" id="caps-lock-warning">
    <normal color="#FFFFFF" alpha="0.5"/>
    <pos anchor="c" x="75%" y="75%" width="box" height="box"/>
    <box orientation="vertical" min-width="400" xpadding="10" ypadding="5" spacing="0">
      <item type="label">
        <normal color="#000000" font="Sans 12"/>
        <pos x="50%" anchor="n"/>
	<!-- Stock label for: You've got capslock on! -->
	<stock type="caps-lock-warning"/>
      </item>
    </box>
  </item>

  <item type="rect">
    <show type="timed"/>
    <normal color="#FFFFFF" alpha="0.5"/>
    <pos anchor="c" x="75%" y="25%" width="box" height="box"/>
    <box orientation="vertical" min-width="400" xpadding="10" ypadding="5" spacing="0">
      <item type="label" id="timed-label">
        <normal color="#000000" font="Sans 12"/>
        <pos x="50%" anchor="n"/>
	<!-- Stock label for: User %s will login in %d seconds -->
	<stock type="timed-label"/>
      </item>
    </box>
  </item>

  <item type="rect" id="userlist-rect">
    <normal color="#FFFFFF" alpha="0.5" font="Sans 14"/>
    <pos anchor="c" x="25%" y="50%" width="box" height="box"/>
    <box orientation="vertical" min-width="440" max-width="440" min-height="100" xpadding="4" ypadding="4" spacing="0">
      <item type="list" id="userlist">
        <pos anchor="nw" x="0" y="0" height="550" width="440"/>
        <color iconcolor="#ACBFDD" labelcolor="#ACBFDD"/>
      </item>
    </box>
  </item>

  <item type="rect">
    <normal color="#FFFFFF" alpha="0.5"/>
    <pos anchor="c" x="75%" y="50%" width="box" height="box"/>
    <box orientation="vertical" min-width="340" xpadding="30" ypadding="30" spacing="10">
      <item type="label">
        <pos anchor="n" x="50%"/>
        <normal color="#000000" font="Sans 18"/>
	<!-- Stock label for: Welcome to %h -->
	<stock type="welcome-label"/>
      </item>
      <item type="label" id="pam-prompt">
        <pos anchor="nw" x="10%"/>
        <normal color="#000000" font="Sans 12"/>
	<!-- Stock label for: Username: -->
	<stock type="username-label"/>
      </item>
      <item type="rect">
	<normal color="#000000"/>
        <pos anchor="n" x="50%" height="24" width="80%"/>
	<fixed>
	  <item type="entry" id="user-pw-entry">
            <normal color="#000000" font="Sans 12"/>
            <pos anchor="nw" x="1" y="1" height="-2" width="-2"/>
	  </item>
	</fixed>
      </item>
      <item type="button" id="ok_button">
        <pos anchor="n" x="50%" height="32" width="50%"/>
        <stock type="ok"/>
      </item>
      <item type="button" id="cancel_button">
        <pos anchor="n" x="50%" height="32" width="50%"/>
        <stock type="startagain"/>
      </item>
      <item type="label" id="pam-message">
        <pos anchor="n" x="50%"/>
        <normal color="#000000" font="Sans 12"/>
	<text></text>
      </item>
    </box>
    <fixed>
      <item type="label" id="pam-error">
        <pos anchor="n" x="50%" y="110%"/>
        <normal color="#000000" font="Sans 12"/>
        <text></text>
      </item>
    </fixed>
  </item>
</greeter>

 I want to edit portions of this like changing the alert/warning for turning on the Caps-lock, etc. but I cant understand the script. I've been trying to look around for tutorials online but aren't any. Can anyone help me about this?

Thanks....

---

### Post by K.Mandla on 2007-08-26
You might dig around on [http://www.gnome.org](http://www.gnome.org), or perhaps even [http://www.gnome-look.org](http://www.gnome-look.org) ... I know there are some customized logins there, so there might be a way to find out how it's done.

---

### Post by mitchi on 2007-08-26
Thanks. gnome-look.org helped a lot by giving me options what gdm themes should look. but i still cant figure out the script layout. if anyone can explain this?

---

### Post by soumo on 2007-10-30
[http://www.5z.com/jirka/gdm-documentation/x1259.html](http://www.5z.com/jirka/gdm-documentation/x1259.html)

Not sure if this is in time, but I had the same problem and this helped loads!

---

