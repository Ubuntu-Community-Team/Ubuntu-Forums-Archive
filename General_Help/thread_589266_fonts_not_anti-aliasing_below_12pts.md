---
title: "fonts not anti-aliasing below 12pts"
date: 2007-10-24
forum: General Help
---

### Post by jon.reeve on 2007-10-24
After I upgraded to Gutsy a few fonts (AR PL fonts) have not been anti-aliasing at under 12pt, and so they're ugly and pixellated (as in the screenshots). I've tried everything I can think to try, and even added a ~/.fonts.conf that looks like this:

```
<?xml version="1.0"?> 
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">

<fontconfig>
	<include ignore_missing="yes">CJK_aliases</include>
	<alias>
		<family>serif</family>
		<prefer>
			<family>Liberation Serif</family>
			<family>Bitstream Vera Serif</family>
			<family>DejaVu Serif</family>
			<family>AR PL UMing CN</family>
			<family>AR PL ShanHeiSun Uni</family>
			<family>AR PL UKai CN</family>
			<family>AR PL ZenKai Uni</family>
		</prefer>
	</alias>
	<alias>
		<family>sans-serif</family>
		<prefer>
			<family>Liberation Sans</family>
			<family>Bitstream Vera Sans</family>
			<family>DejaVu Sans</family>
			<family>AR PL UMing CN</family>
			<family>AR PL ShanHeiSun Uni</family>
			<family>AR PL UKai CN</family>
			<family>AR PL ZenKai Uni</family>
		</prefer>
	</alias>
	<alias>
		<family>monospace</family>
		<prefer>
			<family>Liberation Mono</family>
			<family>Bitstream Vera Sans Mono</family>
			<family>DejaVu Sans Mono</family>
			<family>AR PL UMing CN</family>
			<family>AR PL ShanHeiSun Uni</family>
			<family>WenQuanYi Bitmap Song</family>
			<family>AR PL UKai CN</family>
			<family>AR PL ZenKai Uni</family>
		</prefer>
	</alias>


<!-- makes fonts less than 12 into 12 -->

	<match target="font" >
        <test name="family" compare="contains" >
            <string>SimSun</string>
            <string>AR PL</string>
        </test>
        <test compare="less_eq" name="pixelsize">
            <int>12</int>
        </test>
        <edit mode="assign" name="pixelsize">
            <int>12</int>
        </edit>
    	</match> 

	<match target="font">
        <test name="family" compare="contains" >
            <string>SimSun</string>
            <string>AR PL</string>
        </test>
	<edit name="antialias" mode="assign">
	  <bool>true</bool>
	</edit>
	</match>

</fontconfig>
```

but still nothing seems to be working. I tried editing what I thought would be the appropriate documents in /etc/fonts/conf.d but still to no avail (even in /conf.avail). I've rebooted several times, called 

```
sudo dpkg-reconfigure fontconfig
sudo fc-cache
```

etc. but still having the same problems. Am I just not looking in the right place for Gutsy font configurations?

---

