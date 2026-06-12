---
title: "SDL 2.0 and SDL_Image 2.0, Problems Installing Dependencies"
date: 2017-07-08
forum: General Help
---

### Post by webmanoffesto on 2017-07-08
I'm having trouble installing the SDL 2.0 and SDL_Image 2.0. Please help me resolve this problem.
This is for the Backyard Brains Spike Recorder
[https://github.com/BackyardBrains/Spike-Recorder](https://github.com/BackyardBrains/Spike-Recorder)
[https://github.com/BackyardBrains/Spike-Recorder/blob/master/README.md](https://github.com/BackyardBrains/Spike-Recorder/blob/master/README.md)


This has Dependencies
SDL 2.0 and SDL_Image 2.0
to install this I used "sudo apt-get install libsdl2-2.0"
which seemed to work.


My attempt at installation
```
~/BackyardBrains/NeuralRecorder/Spike-Recorder$ make
~/BackyardBrains/NeuralRecorder/Spike-Recorder$ makeg++ -o src/engine/RecordingManager.o -c src/engine/RecordingManager.cpp -g -O2 -Isrc -Isupport -I. -Wall -DSIGSLOT_PURE_ISO --std=c++11 `sdl2-config --cflags`
/bin/sh: 1: sdl2-config: not found
/bin/sh: 1: g++: not found
Makefile:72: recipe for target 'src/engine/RecordingManager.o' failed
make: *** [src/engine/RecordingManager.o] Error 127

```


I do have the correct files in that directory
```
tom@tom-HP-ProBook-450-G3:~/BackyardBrains/NeuralRecorder/Spike-Recorder$ ls
bass.dll oldlibbass SpikeRecorder.png
bsltext.txt README.md SpikeRecorder.xcodeproj
data SDL2.framework src
libbass.dylib SDL2_image.framework support
macosx-Info.plist SpikeRecorder.entitlements win32-info.rc
Makefile SpikeRecorder.icns win32-installer.nsi
Media.xcassets SpikeRecorder.ico

```

---

### Post by steeldriver on 2017-07-08
When building from source, "dependencies" typically mean development headers and libraries - in this case you probably need to install the **libsdl2-dev** package

```

$ apt-file search sdl2-config
libsdl2-dev: /usr/bin/sdl2-config
libsdl2-dev: /usr/lib/x86_64-linux-gnu/cmake/SDL2/sdl2-config.cmake
libsdl2-dev: /usr/share/man/man1/sdl2-config.1.gz

```

---

### Post by webmanoffesto on 2017-07-08
This seems to say that it is installed
```
$ apt-file search sdl2-config
libsdl2-dev: /usr/bin/sdl2-config
libsdl2-dev: /usr/lib/x86_64-linux-gnu/cmake/SDL2/sdl2-config.cmake
libsdl2-dev: /usr/share/man/man1/sdl2-config.1.gz
```

I seem to have the other dependency installed too
```
$apt-file search libbass
lmms: /usr/lib/x86_64-linux-gnu/lmms/libbassbooster.so

```

---

### Post by steeldriver on 2017-07-08
You'd need to use `dpkg` or `apt-cache` to determine if it's installed

```

apt-cache policy libsdl2-dev

```

---

### Post by webmanoffesto on 2017-07-08
Thanks, now I've installed it. 
```
$ ~/Spike-Recorder$ apt-cache policy libsdl2-devlibsdl2-dev:
  Installed: 2.0.4+dfsg2-1ubuntu1
  Candidate: 2.0.4+dfsg2-1ubuntu1
  Version table:
 *** 2.0.4+dfsg2-1ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu yakkety/universe amd64 Packages
        100 /var/lib/dpkg/status

```

But I'm still having problems
```

~/Spike-Recorder$ make
g++ -o src/widgets/LoadTexture.o -c src/widgets/LoadTexture.cpp -g -O2 -Isrc -Isupport -I. -Wall -DSIGSLOT_PURE_ISO --std=c++11 `sdl2-config --cflags`
src/widgets/LoadTexture.cpp:2:23: fatal error: SDL_image.h: No such file or directory
                       ^
compilation terminated.
Makefile:72: recipe for target 'src/widgets/LoadTexture.o' failed
make: *** [src/widgets/LoadTexture.o] Error 1

~/Spike-Recorder$ apt-file search SDL_image.h
cmake-doc: /usr/share/doc/cmake-data/html/module/FindSDL_image.html
emscripten: /usr/share/emscripten/system/include/SDL/SDL_image.h
libsdl-image1.2-dev: /usr/include/SDL/SDL_image.h
libsdl2-image-dev: /usr/include/SDL2/SDL_image.h

```

---

### Post by mc4man on 2017-07-08
```
sudo apt-get install libsdl2-image-dev libhidapi-dev 
```
Then you'll get to the bigger issues, i.e. a lot of undefined references...

---

### Post by webmanoffesto on 2017-07-08
> **mc4man said:**
> ```
Then you'll get to the bigger issues, i.e. a lot of undefined references...
It seems that you are correct.

It looked like it was installing well but then I got
[CODE]/home/tom/Spike-Recorder/src/ConfigView.cpp:435: _**undefined reference**_ to `BackyardBrains::TouchDropDownList::addItem(std::__cxx11::basic_string<char, std::char_traits<char>, std::allocator<char> > const&)'
collect2: error: ld returned 1 exit status
Makefile:75: recipe for target 'SpikeRecorder' failed
make: *** [SpikeRecorder] Error 1

```

And the program still doesn't run
```
~/Spike-Recorder$ ./SpikeRecorder
bash: ./SpikeRecorder: No such file or directory

```

---

### Post by mc4man on 2017-07-08
That's just the last one, scroll back to where the undefines  start, probably a couple of dozen. Your best bet may be to file an issue on the github page

---

### Post by webmanoffesto on 2017-07-08
Here is the output, I'll file an issue on Github too

Full output at [https://hastebin.com/ijevavebob.pas](https://hastebin.com/ijevavebob.pas)
Github issue posted at [https://github.com/BackyardBrains/Spike-Recorder/issues/9](https://github.com/BackyardBrains/Spike-Recorder/issues/9)

```
~/Spike-Recorder$ makeg++ -o src/widgets/LoadTexture.o -c src/widgets/LoadTexture.cpp -g -O2 -Isrc -Isupport -I. -Wall -DSIGSLOT_PURE_ISO --std=c++11 `sdl2-config --cflags`
g++ -o src/widgets/Label.o -c src/widgets/Label.cpp -g -O2 -Isrc -Isupport -I. -Wall -DSIGSLOT_PURE_ISO --std=c++11 `sdl2-config --cflags`
g++ -o src/widgets/ErrorBox.o -c src/widgets/ErrorBox.cpp -g -O2 -Isrc -Isupport -I. -Wall -DSIGSLOT_PURE_ISO --std=c++11 `sdl2-config --cflags`
g++ -o src/widgets/TextInput.o -c src/widgets/TextInput.cpp -g -O2 -Isrc -Isupport -I. -Wall -DSIGSLOT_PURE_ISO --std=c++11 `sdl2-config --cflags`
src/widgets/TextInput.cpp: In member function &#8216;virtual void BackyardBrains::Widgets::TextInput::keyDownEvent(const SDL_Event&)&#8217;:
src/widgets/TextInput.cpp:246:47: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
             if((_text.size()-_invisibleOffset)>_cursorPosition)
                ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~^~~~~~~~~~~~~~~~
g++ -o src/widgets/RangeSelector.o -c src/widgets/RangeSelector.cpp -g -O2 -Isrc -Isupport -I. -Wall -DSIGSLOT_PURE_ISO --std=c++11 `sdl2-config --cflags`
g++ -o src/widgets/SwitchLayout.o -c src/widgets/SwitchLayout.cpp -g -O2 -Isrc -Isupport -I. -Wall -DSIGSLOT_PURE_ISO --std=c++11 `sdl2-config --cflags`
g++ -o src/widgets/ToolTip.o -c src/widgets/ToolTip.cpp -g -O2 -Isrc -Isupport -I. -Wall -DSIGSLOT_PURE_ISO --std=c++11 `sdl2-config --cflags`
g++ -o src/widgets/Plot.o -c src/widgets/Plot.cpp -g -O2 -Isrc -Isupport -I. -Wall -DSIGSLOT_PURE_ISO --std=c++11 `sdl2-config --cflags`
g++ -o src/widgets/TabBar.o -c src/widgets/TabBar.cpp -g -O2 -Isrc -Isupport -I. -Wall -DSIGSLOT_PURE_ISO --std=c++11 `sdl2-config --cflags`
g++ -o src/DropDownList.o -c src/DropDownList.cpp -g -O2 -Isrc -Isupport -I. -Wall -DSIGSLOT_PURE_ISO --std=c++11 `sdl2-config --cflags`
g++ -o src/Log.o -c src/Log.cpp -g -O2 -Isrc -Isupport -I. -Wall -DSIGSLOT_PURE_ISO --std=c++11 `sdl2-config --cflags`
src/Log.cpp: In constructor &#8216;BackyardBrains::Log::Log()&#8217;:
src/Log.cpp:23:45: warning: format not a string literal and no format arguments [-Wformat-security]
      fprintf(stderr,getLoggingPath().c_str());
                                             ^
g++ -o src/Game.o -c src/Game.cpp -g -O2 -Isrc -Isupport -I. -Wall -DSIGSLOT_PURE_ISO --std=c++11 `sdl2-config --cflags`
g++ -o src/main.o -c src/main.cpp -g -O2 -Isrc -Isupport -I. -Wall -DSIGSLOT_PURE_ISO --std=c++11 `sdl2-config --cflags`
g++ -o src/MainView.o -c src/MainView.cpp -g -O2 -Isrc -Isupport -I. -Wall -DSIGSLOT_PURE_ISO --std=c++11 `sdl2-config --cflags`
g++ -o src/AudioView.o -c src/AudioView.cpp -g -O2 -Isrc -Isupport -I. -Wall -DSIGSLOT_PURE_ISO --std=c++11 `sdl2-config --cflags`
src/AudioView.cpp: In member function &#8216;virtual void BackyardBrains::AudioView::mouseMotionEvent(BackyardBrains::Widgets::MouseEvent*)&#8217;:
src/AudioView.cpp:1231:9: warning: unused variable &#8216;newGain&#8217; [-Wunused-variable]
   float newGain = _prevGain*std::fabs((height()*_channels[_clickedGain].pos-event->pos().y)/(float)_clickedPixelOffset);
         ^~~~~~~
g++ -o src/ConfigView.o -c src/ConfigView.cpp -g -O2 -Isrc -Isupport -I. -Wall -DSIGSLOT_PURE_ISO --std=c++11 `sdl2-config --cflags`
g++ -o src/AnalysisView.o -c src/AnalysisView.cpp -g -O2 -Isrc -Isupport -I. -Wall -DSIGSLOT_PURE_ISO --std=c++11 `sdl2-config --cflags`
src/AnalysisView.cpp: In member function &#8216;void BackyardBrains::AnalysisView::trainDeleted(int)&#8217;:
src/AnalysisView.cpp:265:44: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
     for(int i=_trainList->selectedTrain();i<_spikeTrains.size()-1;i++)
                                           ~^~~~~~~~~~~~~~~~~~~~~~
g++ -o src/AnalysisAudioView.o -c src/AnalysisAudioView.cpp -g -O2 -Isrc -Isupport -I. -Wall -DSIGSLOT_PURE_ISO --std=c++11 `sdl2-config --cflags`
g++ -o src/AnalysisTrainList.o -c src/AnalysisTrainList.cpp -g -O2 -Isrc -Isupport -I. -Wall -DSIGSLOT_PURE_ISO --std=c++11 `sdl2-config --cflags`
src/AnalysisTrainList.cpp: In member function &#8216;void BackyardBrains::AnalysisTrainList::setInitialSelection()&#8217;:
src/AnalysisTrainList.cpp:30:22: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
     for(int st = 0;st<_spikeTrains.size()-1;st++)
                    ~~^~~~~~~~~~~~~~~~~~~~~~
src/AnalysisTrainList.cpp: In member function &#8216;virtual void BackyardBrains::AnalysisTrainList::paintEvent()&#8217;:
src/AnalysisTrainList.cpp:92:21: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
                 if(i==_selectedTrain && _spikeTrains[i].channelIndex == channelIndex)
                    ~^~~~~~~~~~~~~~~~
src/AnalysisTrainList.cpp:130:21: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
                 if(i==_selectedTrain && _selectedTrain != (int)_spikeTrains.size()-1 && _spikeTrains[i].channelIndex == channelIndex)
                    ~^~~~~~~~~~~~~~~~
src/AnalysisTrainList.cpp: In member function &#8216;virtual void BackyardBrains::AnalysisTrainList::mousePressEvent(BackyardBrains::Widgets::MouseEvent*)&#8217;:
src/AnalysisTrainList.cpp:183:52: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
                 for(int tempSTIndex = 0;tempSTIndex<_spikeTrains.size();tempSTIndex++)
                                         ~~~~~~~~~~~^~~~~~~~~~~~~~~~~~~~
g++ -o src/AnalysisPlots.o -c src/AnalysisPlots.cpp -g -O2 -Isrc -Isupport -I. -Wall -DSIGSLOT_PURE_ISO --std=c++11 `sdl2-config --cflags`
g++ -o src/RecordingBar.o -c src/RecordingBar.cpp -g -O2 -Isrc -Isupport -I. -Wall -DSIGSLOT_PURE_ISO --std=c++11 `sdl2-config --cflags`
g++ -o src/ColorDropDownList.o -c src/ColorDropDownList.cpp -g -O2 -Isrc -Isupport -I. -Wall -DSIGSLOT_PURE_ISO --std=c++11 `sdl2-config --cflags`
g++ -o src/FFTView.o -c src/FFTView.cpp -g -O2 -Isrc -Isupport -I. -Wall -DSIGSLOT_PURE_ISO --std=c++11 `sdl2-config --cflags`
g++ -o src/ThresholdPanel.o -c src/ThresholdPanel.cpp -g -O2 -Isrc -Isupport -I. -Wall -DSIGSLOT_PURE_ISO --std=c++11 `sdl2-config --cflags`
g++ -o src/widgets/native/FileDialogLinux.o -c src/widgets/native/FileDialogLinux.cpp -g -O2 -Isrc -Isupport -I. -Wall -DSIGSLOT_PURE_ISO --std=c++11 `sdl2-config --cflags`
g++ -o src/native/PathsLinux.o -c src/native/PathsLinux.cpp -g -O2 -Isrc -Isupport -I. -Wall -DSIGSLOT_PURE_ISO --std=c++11 `sdl2-config --cflags`
g++ -o SpikeRecorder src/engine/RecordingManager.o src/engine/AnalysisManager.o src/engine/FileRecorder.o src/engine/Player.o src/engine/ArduinoSerial.o src/engine/SpikeSorter.o src/engine/SpikeAnalysis.o src/engine/BASSErrors.o src/engine/FileReadUtil.o src/engine/FFTBackend.o src/engine/HIDUsbManager.o src/engine/EkgBackend.o src/engine/FilterBase.o src/engine/HighPassFilter.o src/engine/LowPassFilter.o src/engine/NotchFilter.o src/widgets/LayoutItem.o src/widgets/BoxLayout.o src/widgets/Widget.o src/widgets/Painter.o src/widgets/PushButton.o src/widgets/DropDownList.o src/widgets/ScrollBar.o src/widgets/Application.o src/widgets/BitmapFontGL.o src/widgets/TextureGL.o src/widgets/LoadTexture.o src/widgets/Label.o src/widgets/ErrorBox.o src/widgets/TextInput.o src/widgets/RangeSelector.o src/widgets/SwitchLayout.o src/widgets/ToolTip.o src/widgets/Plot.o src/widgets/TabBar.o src/DropDownList.o src/Log.o src/Game.o src/main.o src/MainView.o src/AudioView.o src/ConfigView.o src/AnalysisView.o src/AnalysisAudioView.o src/AnalysisTrainList.o src/AnalysisPlots.o src/RecordingBar.o src/ColorDropDownList.o src/FFTView.o src/ThresholdPanel.o src/widgets/native/FileDialogLinux.o src/native/PathsLinux.o -g -O2 -Isrc -Isupport -I. -Wall -DSIGSLOT_PURE_ISO --std=c++11 `sdl2-config --cflags` `sdl2-config --libs` -lSDL2_image -lGL -lGLU -lbass -lpthread -lhidapi-libusb
src/engine/RecordingManager.o: In function `BackyardBrains::RecordingManager::makeNewSerialAudioConfig(std::__cxx11::basic_string<char, std::char_traits<char>, std::allocator<char> >)':
/home/tom/BackyardBrains/NeuralRecorder/Spike-Recorder/src/engine/RecordingManager.cpp:2508: undefined reference to `BackyardBrains::AudioInputConfig::AudioInputConfig()'
/home/tom/BackyardBrains/NeuralRecorder/Spike-Recorder/src/engine/RecordingManager.cpp:2508: undefined reference to `BackyardBrains::AudioInputConfig::~AudioInputConfig()'
/home/tom/BackyardBrains/NeuralRecorder/Spike-Recorder/src/engine/RecordingManager.cpp:2508: undefined reference to `BackyardBrains::AudioInputConfig::~AudioInputConfig()'
src/engine/RecordingManager.o: In function `BackyardBrains::RecordingManager::RecordingManager()':
/home/tom/BackyardBrains/NeuralRecorder/Spike-Recorder/src/engine/RecordingManager.cpp:22: undefined reference to `BackyardBrains::AudioInputConfig::AudioInputConfig()'
/home/tom/BackyardBrains/NeuralRecorder/Spike-Recorder/src/engine/RecordingManager.cpp:22: undefined reference to `BackyardBrains::AudioInputConfig::~AudioInputConfig()'
/home/tom/BackyardBrains/NeuralRecorder/Spike-Recorder/src/engine/RecordingManager.cpp:22: undefined reference to `BackyardBrains::AudioInputConfig::~AudioInputConfig()'
src/engine/RecordingManager.o: In function `BackyardBrains::RecordingManager::~RecordingManager()':
/home/tom/BackyardBrains/NeuralRecorder/Spike-Recorder/src/engine/RecordingManager.cpp:71: undefined reference to `BackyardBrains::AudioInputConfig::~AudioInputConfig()'
src/engine/RecordingManager.o: In function `void __gnu_cxx::new_allocator<std::_List_node<BackyardBrains::AudioInputConfig> >::destroy<BackyardBrains::AudioInputConfig>(BackyardBrains::AudioInputConfig*)':
/usr/include/c++/6/ext/new_allocator.h:124: undefined reference to `BackyardBrains::AudioInputConfig::~AudioInputConfig()'
src/ConfigView.o: In function `BackyardBrains::ConfigView::colorChanged(int, int)':
/home/tom/Spike-Recorder/src/ConfigView.cpp:1172: undefined reference to `BackyardBrains::HorizontalColorPicker::setSelectionSilent(int)'
src/ConfigView.o: In function `BackyardBrains::ConfigView::calibratePressed()':
/home/tom/Spike-Recorder/src/ConfigView.cpp:1197: undefined reference to `BackyardBrains::CalibrationWindow::CalibrationWindow(BackyardBrains::RecordingManager&, BackyardBrains::AudioView&, BackyardBrains::Widgets::Widget*)'
src/ConfigView.o: In function `BackyardBrains::ConfigView::connectPressed()':
/home/tom/Spike-Recorder/src/ConfigView.cpp:937: undefined reference to `BackyardBrains::TouchDropDownList::selection() const'
/home/tom/Spike-Recorder/src/ConfigView.cpp:1002: undefined reference to `BackyardBrains::TouchDropDownList::setDisabled(bool)'
src/ConfigView.o: In function `BackyardBrains::ConfigView::SetupScreen()':
/home/tom/Spike-Recorder/src/ConfigView.cpp:289: undefined reference to `BackyardBrains::HorizontalColorPicker::HorizontalColorPicker(BackyardBrains::Widgets::Widget*)'
/home/tom/Spike-Recorder/src/ConfigView.cpp:293: undefined reference to `BackyardBrains::HorizontalColorPicker::setContent(std::vector<BackyardBrains::Widgets::Color, std::allocator<BackyardBrains::Widgets::Color> > const&)'
/home/tom/Spike-Recorder/src/ConfigView.cpp:363: undefined reference to `BackyardBrains::HorizontalColorPicker::setSelection(int)'
/home/tom/Spike-Recorder/src/ConfigView.cpp:297: undefined reference to `BackyardBrains::HorizontalColorPicker::setContent(std::vector<BackyardBrains::Widgets::Color, std::allocator<BackyardBrains::Widgets::Color> > const&)'
/home/tom/Spike-Recorder/src/ConfigView.cpp:406: undefined reference to `BackyardBrains::TouchDropDownList::TouchDropDownList(BackyardBrains::Widgets::Widget*, int, int)'
/home/tom/Spike-Recorder/src/ConfigView.cpp:408: undefined reference to `BackyardBrains::TouchDropDownList::clear()'
/home/tom/Spike-Recorder/src/ConfigView.cpp:417: undefined reference to `BackyardBrains::TouchDropDownList::addItem(std::__cxx11::basic_string<char, std::char_traits<char>, std::allocator<char> > const&)'
/home/tom/Spike-Recorder/src/ConfigView.cpp:443: undefined reference to `BackyardBrains::TouchDropDownList::setSelection(int)'
/home/tom/Spike-Recorder/src/ConfigView.cpp:448: undefined reference to `BackyardBrains::TouchDropDownList::setDisabled(bool)'
/home/tom/Spike-Recorder/src/ConfigView.cpp:590: undefined reference to `BackyardBrains::HorizontalNumberPicker::HorizontalNumberPicker(BackyardBrains::Widgets::Widget*)'
/home/tom/Spike-Recorder/src/ConfigView.cpp:592: undefined reference to `BackyardBrains::HorizontalNumberPicker::setSelection(int)'
/home/tom/Spike-Recorder/src/ConfigView.cpp:423: undefined reference to `BackyardBrains::TouchDropDownList::addItem(std::__cxx11::basic_string<char, std::char_traits<char>, std::allocator<char> > const&)'
/home/tom/Spike-Recorder/src/ConfigView.cpp:429: undefined reference to `BackyardBrains::TouchDropDownList::addItem(std::__cxx11::basic_string<char, std::char_traits<char>, std::allocator<char> > const&)'
/home/tom/Spike-Recorder/src/ConfigView.cpp:435: undefined reference to `BackyardBrains::TouchDropDownList::addItem(std::__cxx11::basic_string<char, std::char_traits<char>, std::allocator<char> > const&)'
collect2: error: ld returned 1 exit status
Makefile:75: recipe for target 'SpikeRecorder' failed
make: *** [SpikeRecorder] Error 1
tom@tom-HP-ProBook-450-G3:~/Spike-Recorder$ ./SpikeRecorder
bash: ./SpikeRecorder: No such file or directory



```

---

### Post by webmanoffesto on 2017-07-11
[COLOR=#24292E][FONT=-apple-system]A final version of the working code with an edited OBJECTS list in Makefile is here [/FONT][/COLOR][https://hastebin.com/lahapahule.tex](https://hastebin.com/lahapahule.tex)

---

