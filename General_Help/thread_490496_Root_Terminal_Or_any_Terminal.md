---
title: "Root Terminal Or any Terminal"
date: 2007-07-02
forum: General Help
---

### Post by derby007 on 2007-07-02
How do I get my ROOT termnal or any terminal/console to open up at a desired 'width-height' ?

---

### Post by Brucevdk on 2007-07-02
[LIST]
[*][ Change default size of gnome-terminal?]("http://ubuntuforums.org/showthread.php?t=251556")
[/LIST]
> **ayoli said:**
> create a launcher (or edit menu entry with alacarte) that launches gnome term like this:
```
gnome-terminal --geometry 420x64
```
replace values by yours.

I personally use [Devil's Pie]("http://burtonini.com/blog/computers/devilspie") to maximize any gnome-terminal, see [the GNOME Live! wiki for more information]("http://live.gnome.org/DevilsPie").
```

sudo apt-get install devilspie
cat > ~/.devilspie/terminal.ds << EOT
(if (is (application_name) "Terminal")
	(maximize "TRUE")
)
EOT
devilspie &

```

---

