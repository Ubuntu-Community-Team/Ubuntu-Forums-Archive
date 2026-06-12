---
title: "my-weather-indicator startup failure"
date: 2015-01-13
forum: General Help
---

### Post by shochatd on 2015-01-13
my-weather-indicator seems to have stopped working. So I tried running it at the command line to look for error messages. I got the following traceback:
[FONT=Courier New]Traceback (most recent call last):
  File "/opt/extras.ubuntu.com/my-weather-indicator/bin/my-weather-indicator", line 50, in <module>
    mwi=MWI()
  File "/opt/extras.ubuntu.com/my-weather-indicator/share/my-weather-indicator/myweatherindicator.py", line 135, in __init__
    self.load_preferences()
  File "/opt/extras.ubuntu.com/my-weather-indicator/share/my-weather-indicator/myweatherindicator.py", line 376, in load_preferences
    self.work()
  File "/opt/extras.ubuntu.com/my-weather-indicator/share/my-weather-indicator/myweatherindicator.py", line 200, in work
    self.set_menu()
  File "/opt/extras.ubuntu.com/my-weather-indicator/share/my-weather-indicator/myweatherindicator.py", line 512, in set_menu
    weather = self.weatherservice1.get_weather()
  File "/opt/extras.ubuntu.com/my-weather-indicator/share/my-weather-indicator/wopenweathermapapi.py", line 236, in get_weather
    direction = data['deg']
KeyError: 'deg'
[/FONT]I tried deleting [FONT=Courier New]~/.config/my-weather-indicator/my-weather-indicator.conf[/FONT]: It comes up briefly, presenting a screen for setting preferences, but as soon as I click OK, it fails with the same traceback. I'm wondering if a recent python update might be to blame.

---

