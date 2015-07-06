# Docker container for NativeScript development

## Content

* [why](#why)
* [Setup](#setup)
* [New Project](#new-project)
* [Useful commands](#useful-commands)
* [References](#references)

## Why?

I don't want to install and configure Java, Android SDK, Ant, cordova etc.. life is too short.

## Setup

    git clone git@github.com:oren/docker-nativescript.git
    cd docker-nativescript
    docker build -t nativescript .
    alias mine='sudo chown -R $USER'
    alias tns='docker run -it --rm --privileged -v /dev/bus/usb:/dev/bus/usb -v $PWD:/src nativescript tns'

The alias command lets you use `cordova` for running any command inside the cordova container.

## New Project

    tns create hello
    cd hello
    tns platform add android
    tns run android

Connect your android device to your laptop with a usb

    cordova run android

That's it, your app should be on your phone!

## Useful commands

List of attached devices. make sure you see your phone in that list.

    docker run --rm -i -v $(pwd):/workspace -w /workspace --privileged -v /dev/bus/usb:/dev/bus/usb tns devices

## References

The image is based on https://github.com/Kallikrein/dockerfiles/tree/master/android-cordova~/projects/myAPP
