juicy
=====
[![Gem Version](https://badge.fury.io/rb/juicy.svg)](http://badge.fury.io/rb/juicy)
[![Build Status](https://travis-ci.org/RSMP/juicy.svg)](https://travis-ci.org/RSMP/juicy)
[![Coverage Status](https://coveralls.io/repos/RSMP/juicy/badge.png)](https://coveralls.io/r/RSMP/juicy)
[![Dependency Status](https://gemnasium.com/RSMP/juicy.svg)](https://gemnasium.com/RSMP/juicy)
[![Code Climate](https://codeclimate.com/github/RSMP/juicy/badges/gpa.svg)](https://codeclimate.com/github/RSMP/juicy)

Song creation software for the Ruby developer

Simply

    gem install juicy

Some Examples
=====
To make a pitch, give it a frequency.
By default, the frequency will be tuned to the nearest
frequency in equal temperament.

    require 'juicy'
    pitch = Juicy::Pitch.new(445)
    pitch.play # audio playback only implemented for Windows and Linux platforms
    # Linux platforms need to have ALSA audio libraries installed (which you probably do)

A Note is a Pitch with a name.
You give it a note name and an octave

    note = Juicy::Note.new(name: "G#", octave_change: -1)
    note.play

You can also add or subtract from a note to go to the next half step

    note += 1
    note.play
    note -= 2
    note.play

With this much, you can make your own scales!

    note = Juicy::Note.new(name: "C")
    major_scale = [2,2,1,2,2,2,1]
    major_scale.each do |step|
      puts note
      note.play
      note += step
    end
    note.play

Of course, this is cumbersome to do all on our own,
so you have a Scale available to you.

    root = Juicy::Note.new(name: "D", octave_change: -1)
    scale = Juicy::Scale.new(mode: :major, root: root)
    scale.each_note do |note|
      note.play
    end

While there is enough here to write out your own scales,
current development work is being done on scale objects
and a beat sequencer to bring it all together.

Be sure to check in later for new features and updates!
