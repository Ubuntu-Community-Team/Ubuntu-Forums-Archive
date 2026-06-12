---
title: "I need some help with sed"
date: 2006-11-22
forum: General Help
---

### Post by an.echte.trilingue on 2006-11-22
I am trying to write a little script that optimizes xml files so that they render faster by putting all the tags on a single line, removing comments, and removing white space between tags.  I am trying to use sed to do this.

Where I am having trouble is removing the white spaces between tags.

To illustrate what I mean, I want something like this to go in:

[HTML]<tag 1>  <!--comment 1-->
  <tag 2>  <!--comment 2-->
    <tag 3/>
  </tag 2>
</tag 1>[/HTML]

and something like this to come out:

[HTML]<tag 1><tag 2><tag 3/></tag 2></tag 1>[/HTML]

Right now I can remove the line breaks with this:

```
sed -e :a -e '$!N;s/\n/ /;ta' -e 'P;D' $FILENAME > step1
```

And I can remove the comments with this:

```
sed 's/<!--'.*'-->//g' step1 > step2
```

Which gives me this:

[HTML]<tag 1>    <tag 2>      <tag 3/>  </tag 2></tag 1>[/HTML]

But I cannot figure out how to take out the white spaces.

Does anybody know how to do this?

Thanks for your time

-mat

---

### Post by Ramses de Norre on 2006-11-22
This should do:
```
sed -e 's/>[[:space:]]</></g' $FILENAME
```
But I only tested it on the little piece of text you gave, so please test it decently before you let it replace all your xml files.

---

### Post by an.echte.trilingue on 2006-11-22
OK.  That does not quite work.  I will give a better example.  I am working on a GDM theme but it is really huge and to get it to render faster I need to strip all the extra stuff out of the file.  I don't want to do this by hand because it takes an hour or so and if I want to change anything I have to go back to the commented version to make any changes and then remove everything again.

So, for sake of example, let's take the happygnome gdm theme's xml file.

[HTML]<?xml version="1.0" encoding="UTF-8"?>
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
    <pos x="-160" y="-37" anchor="e"/>
    <text>%c</text>
  </item>

  <item type="rect" id="caps-lock-warning">
    <normal color="#FFFFFF" alpha="0.5"/>
    <pos anchor="c" x="50%" y="75%" width="box" height="box"/>
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
    <pos anchor="c" x="50%" y="25%" width="box" height="box"/>
    <box orientation="vertical" min-width="400" xpadding="10" ypadding="5" spacing="0">
      <item type="label" id="timed-label">
        <normal color="#000000" font="Sans 12"/>
        <pos x="50%" anchor="n"/>
	<!-- Stock label for: User %s will login in %d seconds -->
	<stock type="timed-label"/>
      </item>
    </box>
  </item>

  <item type="rect">
    <normal color="#FFFFFF" alpha="0.5"/>
    <pos anchor="c" x="50%" y="50%" width="box" height="box"/>
    <box orientation="vertical" min-width="340" xpadding="30" ypadding="30" spacing="10">
      <item type="label">
        <pos anchor="n" x="50%"/>
        <normal color="#000000" font="Sans 14"/>
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
</greeter>[/HTML]

First I strip the comments:

```
sed 's/<!--'.*'-->//' happygnome.xml > step1 
```

This seems to work fine:

[HTML]<?xml version="1.0" encoding="UTF-8"?>
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
    <pos x="-160" y="-37" anchor="e"/>
    <text>%c</text>
  </item>

  <item type="rect" id="caps-lock-warning">
    <normal color="#FFFFFF" alpha="0.5"/>
    <pos anchor="c" x="50%" y="75%" width="box" height="box"/>
    <box orientation="vertical" min-width="400" xpadding="10" ypadding="5" spacing="0">
      <item type="label">
        <normal color="#000000" font="Sans 12"/>
        <pos x="50%" anchor="n"/>
	
	<stock type="caps-lock-warning"/>
      </item>
    </box>
  </item>

  <item type="rect">
    <show type="timed"/>
    <normal color="#FFFFFF" alpha="0.5"/>
    <pos anchor="c" x="50%" y="25%" width="box" height="box"/>
    <box orientation="vertical" min-width="400" xpadding="10" ypadding="5" spacing="0">
      <item type="label" id="timed-label">
        <normal color="#000000" font="Sans 12"/>
        <pos x="50%" anchor="n"/>
	
	<stock type="timed-label"/>
      </item>
    </box>
  </item>

  <item type="rect">
    <normal color="#FFFFFF" alpha="0.5"/>
    <pos anchor="c" x="50%" y="50%" width="box" height="box"/>
    <box orientation="vertical" min-width="340" xpadding="30" ypadding="30" spacing="10">
      <item type="label">
        <pos anchor="n" x="50%"/>
        <normal color="#000000" font="Sans 14"/>
	
	<stock type="welcome-label"/>
      </item>
      <item type="label" id="pam-prompt">
        <pos anchor="nw" x="10%"/>
        <normal color="#000000" font="Sans 12"/>
	
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
</greeter>[/HTML]

Then I put everything on one line:

```
sed -e :a -e '$!N;s/\n/ /;ta' -e 'P;D' step1 > step2
```

Which also seems to work fine:
[HTML]<?xml version="1.0" encoding="UTF-8"?> <!DOCTYPE greeter SYSTEM "greeter.dtd"> <greeter>   <item type="svg">     <normal file="background.svg"/>     <pos x="0" y="0" width="100%" height="-75"/>   </item>   <item type="rect">     <normal color="#000000"/>     <pos x="0" y="-75" width="100%" height="75"/>     <fixed>       <item type="rect">         <normal color="#ffffff"/>         <pos x="0" y="4" width="100%" height="100%"/>         <box orientation="horizontal" spacing="10" xpadding="10" ypadding="10">           <item type="button" id="options_button">             <pos width="100" height="50" />             <stock type="options"/>           </item>         </box>       </item>     </fixed>   </item>   <item type="svg">     <normal file="gnome-logo.svg"/>     <pos x="-12" y="-12" width="30" height="47" anchor="se" />   </item>   <item type="label" id="clock">     <normal color="#000000" font="Sans 12"/>     <pos x="-160" y="-37" anchor="e"/>     <text>%c</text>   </item>    <item type="rect" id="caps-lock-warning">     <normal color="#FFFFFF" alpha="0.5"/>     <pos anchor="c" x="50%" y="75%" width="box" height="box"/>     <box orientation="vertical" min-width="400" xpadding="10" ypadding="5" spacing="0">       <item type="label">         <normal color="#000000" font="Sans 12"/>         <pos x="50%" anchor="n"/> 	 	<stock type="caps-lock-warning"/>       </item>     </box>   </item>    <item type="rect">     <show type="timed"/>     <normal color="#FFFFFF" alpha="0.5"/>     <pos anchor="c" x="50%" y="25%" width="box" height="box"/>     <box orientation="vertical" min-width="400" xpadding="10" ypadding="5" spacing="0">       <item type="label" id="timed-label">         <normal color="#000000" font="Sans 12"/>         <pos x="50%" anchor="n"/> 	 	<stock type="timed-label"/>       </item>     </box>   </item>    <item type="rect">     <normal color="#FFFFFF" alpha="0.5"/>     <pos anchor="c" x="50%" y="50%" width="box" height="box"/>     <box orientation="vertical" min-width="340" xpadding="30" ypadding="30" spacing="10">       <item type="label">         <pos anchor="n" x="50%"/>         <normal color="#000000" font="Sans 14"/> 	 	<stock type="welcome-label"/>       </item>       <item type="label" id="pam-prompt">         <pos anchor="nw" x="10%"/>         <normal color="#000000" font="Sans 12"/> 	 	<stock type="username-label"/>       </item>       <item type="rect"> 	<normal color="#000000"/>         <pos anchor="n" x="50%" height="24" width="80%"/> 	<fixed> 	  <item type="entry" id="user-pw-entry">             <normal color="#000000" font="Sans 12"/>             <pos anchor="nw" x="1" y="1" height="-2" width="-2"/> 	  </item> 	</fixed>       </item>       <item type="label" id="pam-message">         <pos anchor="n" x="50%"/>         <normal color="#000000" font="Sans 12"/> 	<text></text>       </item>     </box>     <fixed>       <item type="label" id="pam-error">         <pos anchor="n" x="50%" y="110%"/>         <normal color="#000000" font="Sans 12"/>         <text></text>       </item>     </fixed>   </item> </greeter>  
[/HTML]

But then removing the spaces is where the hang up is:

```
sed -e 's/>[[:space:]]</></g' step2 > step3
```

Does not seem to do anything, either...

Any other ideas?

Thank you for your time.
-mat

---

### Post by Ramses de Norre on 2006-11-22
Hmm, indeed, it only removed one space.. How about these ones?
```
sed -e 's/>[ ^t]*</></g' $FILENAME
```
Or
```
sed -e 's/>[[:space:]]*</></g' $FILENAME
```

It seems like both of them work.

---

### Post by an.echte.trilingue on 2006-11-22
That did it.

Thank you for your time.  I was pulling my hair out with the man pages and the tutorials on the net.  Talk about a learning curve.  Sheesh.

Thanks
-mat

---

### Post by Ramses de Norre on 2006-11-22
Yeah there is definitely a pretty steep learning curve with sed ;) But it's an incredibly powerful tool like you probably noticed.

---

