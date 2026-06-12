---
title: "Help! Ubuntu Edgy got ugly after a simple update"
date: 2007-02-15
forum: General Help
---

### Post by vintage-vinnie on 2007-02-15
I used to have beautiful anti-aliased fonts but now I have nothing!
firefox is ugly and look how messed up my term looks!

can someone help me?

I changed my ~.fonts.conf file to this and it did nothing!

```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>

	<!-- Replace Courier with a better-looking font -->
	<match target="pattern" name="family">
		<test name="family" qual="any">
			<string>Courier</string>
		</test>
		<edit name="family" mode="assign">
			<!-- Other choices - Courier New, Luxi Mono -->
			<string>Verdana</string>
		</edit>
	</match>

	<match target="font">
		<edit name="rgba" mode="assign">
			<const>rgb</const>
		</edit>
		<edit name="autohint" mode="assign">
			<bool>true</bool>
		</edit>
		<edit name="antialias" mode="assign">
			<bool>true</bool>
		</edit>
		<edit name="hinting" mode="assign">
			<bool>true</bool>
		</edit>
		<edit name="hintstyle" mode="assign">
			<const>full</const>
		</edit>
	</match>

	<!-- Disable autohint for bold fonts, otherwise they look *too* bold -->
	<match target="font">
   		<test name="weight" compare="more">
			<const>light</const>
		</test>
   		<edit name="autohint" mode="assign">
			<bool>false</bool>
		</edit>
	</match>

	<!-- Reject bitmap fonts in favour of Truetype, Postscript, etc. -->
	<selectfont>
		<rejectfont>
			<pattern>
				<patelt name="scalable">
					<bool>false</bool>
				</patelt>
			</pattern>
		</rejectfont>
	</selectfont>

</fontconfig>
```

---

### Post by vintage-vinnie on 2007-02-16
Nevermind. I just had to reset my /etc/fonts/local.conf

problem solved

---

### Post by db9s on 2007-02-18
help! how did you do it? I don't have a local.conf, I'm tired of Firefox's ugly fonts

---

### Post by llamakc on 2007-02-18
Bump. Please explain what you did to 'fix' it for others.

---

### Post by llamakc on 2007-02-18
> **llamakc said:**
> Bump. Please explain what you did to 'fix' it for others.

Looks like the OP created the /etc/fonts/local.conf file with the contents of his above post. 

Give that a try and restart X. Impressive.

---

