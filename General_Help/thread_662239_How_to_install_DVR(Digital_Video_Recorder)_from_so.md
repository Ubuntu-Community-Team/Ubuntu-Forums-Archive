---
title: "How to install DVR(Digital Video Recorder) from source?"
date: 2008-01-08
forum: General Help
---

### Post by chunchengch on 2008-01-08
I installed the DVR package in Synaptic, but it did not work normally, so I download the latest version of DVR dvr-3.99.3 from [http://www.pierrox.net/dvr/](http://www.pierrox.net/dvr/), the problem is I have to edit the makefile myself, however, I never did it before, so it really bothers me, can anyone help this? thanks a lot!

I am using Ubuntu 7.10 and the packages qt3-dev-tools (3:3.3.8really3.3.7-0ubuntu1.1) and gstreamer0.10 are installed.


Here is the content of makefile:

# edit these values to match your system
PREFIX=/usr/local
QT_INCLUDE=-I/usr/include/qt
QT_LIB=-L/usr/lib/qt -lqt-mtgstreamer
GST_INCLUDE=$(shell pkg-config --cflags gstreamer-0.10)
GST_LIB=$(shell pkg-config --libs gstreamer-0.10)

DVR_VERSION=3.99.3

BUILD=../build

CFLAGS_ADD=-g
LDFLAGS_ADD=
CFLAGS=-DPREFIX="\"$(PREFIX)\"" -DDVR_VERSION="\"$(DVR_VERSION)\"" -W -Wall -I. -I$(BUILD) $(QT_INCLUDE) $(GST_INCLUDE) $(CFLAGS_ADD)
CXXFLAGS=$(CFLAGS)
LDFLAGS=$(QT_LIB) $(GST_LIB) $(LDFLAGS_ADD)

exe=dvr

ui=dvr_control.ui tab_audio_config.ui tab_codec_config.ui tab_general.ui tab_video_config.ui tab_monitoring.ui device_selection.ui property_editor.ui

ui_o=$(ui:%.ui=$(BUILD)/ui_%.o)
moc_o=$(ui:%.ui=$(BUILD)/moc_%.o)

objs=$(BUILD)/main.o \
     $(BUILD)/dvr.o \
     $(BUILD)/dvr_control.o \
     $(BUILD)/device_selection.o \
     $(BUILD)/tab_general.o \
     $(BUILD)/tab_audio_config.o \
     $(BUILD)/tab_codec_config.o \
     $(BUILD)/tab_video_config.o \
     $(BUILD)/tab_monitoring.o \
     $(BUILD)/property_editor.o \
     $(BUILD)/qlistbox_codec.o \
     $(BUILD)/qlistview_codec_property.o


all: init $(BUILD)/$(exe)

$(BUILD)/$(exe): $(ui:%.ui=$(BUILD)/ui_%.h) $(ui:%.ui=$(BUILD)/ui_%.cpp) $(objs:%.o=%.d) $(ui_o) $(moc_o) $(objs)
	g++ $(LDFLAGS) $(ui_o) $(moc_o) $(objs) -o $@
		  
init:
	mkdir -p $(BUILD)

$(BUILD)/%.o: %.cpp
	g++ -c -o $@ $*.cpp $(CXXFLAGS)

$(BUILD)/%.o: %.c
	gcc -c -o $@ $*.c $(CFLAGS)

$(BUILD)/%.o: $(BUILD)/%.cpp
	g++ -c -o $@ $(BUILD)/$*.cpp $(CXXFLAGS)

$(BUILD)/ui_%.h: %.ui
	uic $^ > $@

$(BUILD)/ui_%.cpp: $(BUILD)/ui_%.h
	uic -impl $< $*.ui > $@
	
$(BUILD)/moc_%.cpp: $(BUILD)/ui_%.h
	moc $^ -o $@

$(BUILD)/%.d: %.c
	cpp -MM $(CXXFLAGS) -MT $(BUILD)/$*.o $^ > $@ || (rm -f $@; exit 1)

$(BUILD)/%.d: %.cpp
	cpp -MM $(CXXFLAGS) -MT $(BUILD)/$*.o $^ > $@ || (rm -f $@; exit 1)

clean:
	rm -rf *~ $(BUILD)

dep: $(objs:%.o=%.d)

i18n_update: *.cpp $(ui)
	for l in de fr; do lupdate $^ -ts translations/dvr_$$l.ts; done

i18n_release:
	for l in de fr; do lrelease $^ translations/dvr_$$l.ts -qm $(BUILD)/dvr_$$l.qm; done

install: $(BUILD)/$(exe) i18n_release
	install -d -m 755 ${PREFIX}/bin
	install -d -m 755 ${PREFIX}/share/dvr-${DVR_VERSION}/translations
	install -d -m 755 ${PREFIX}/share/dvr-${DVR_VERSION}/doc
	install -s -m 755 $(BUILD)/$(exe) ${PREFIX}/bin
	install -m 644 $(BUILD)/*.qm ${PREFIX}/share/dvr-${DVR_VERSION}/translations
	install -m 644 ../doc/* ${PREFIX}/share/dvr-${DVR_VERSION}/doc

-include $(BUILD)/*.d

---

