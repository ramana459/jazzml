JAZZML: Statistical Jazz Improvisation
======

Final project for COS 401: Introduction to Machine Translation. Computer jazz improvisation powered by machine learning,
specifically trigram modeling, K-Means clustering, and chord inference with SVMs.

Messy code + needs to be better modularized.

Dependencies:
<ul>
  <li>NumPy</li>
  <li>SciPy</li>
  <li>Pandas</li>
  <li>Scikit-Learn</li>
  <li>Matplotlib</li>
</ul>

In addition, you'll need a couple of specialized music libraries for Python:

<ul>
  <li>music21 - for MIDI data extraction</li>
  <li>mingus (https://code.google.com/p/mingus/) - for playback</li>
  <li>fluidsynth - for playback</li>
</ul>

----------

If you're new here: Included is a sample MIDI file (Oscar-Peterson-2.mid) for analysis and generation. For a quick demo, go to the subdirectory "./oscar/oscar2" and run things in this order (assuming you have the dependencies):

First, run the script oscar2.py as:

$ python oscar2.py > oscar2chords.txt
(or $ python oscar2.py > oscar2notes.txt based on stdin)

This should give you two data files which represent the chords and the notes encoded in the original MIDI file: oscar2chords.txt, and oscar2notes.txt.

Next, to generate new notes with the N-Gram model, run iPython notebook <b>6a: The N-Gram Pipeline, Part I</b> which writes out the n-grams to the file oscar2ngrams.txt.

Next, to generate the chord classifier (SVM) with chord notes, first run iPython notebook <b>5: Extract Chords</b> to process the raw data in oscar2chords.txt, clean it up, and write it out to oscar2chords_extract.txt. Then run iPython notebook <b>7: Predictive Chord Modeling with Bitwise Note Vectors</b>, which reads in that just-created file, trains an SVM to return those chords based on consonant pentatonic notes (semirandomly generated), and cPickles that SVM to disk.

Finally, for chord accompaniment and dynamic playback, run notebook <b>6b: The N-Gram Pipeline, Part II</b>.
