## Summary ##

This library provides a text mode progressbar. This is tipically used to display the progress of a long running operation, providing a visual clue that processing is underway.

The `ProgressBar` class manages the progress, and the format of the line is given by a number of widgets. A widget is an object that may display diferently depending on the state of the progress. There are three types of widget:

  * a string, which always shows itself;
  * a `ProgressBarWidget`, which may return a diferent value every time it's update method is called; and
  * a `ProgressBarWidgetHFill`, which is like `ProgressBarWidget`, except it expands to fill the remaining width of the line.

The `progressbar` module is very easy to use, yet very powerful. And automatically supports features like auto-resizing when available.

## Examples ##

Using the progress bar as an iterable:
```
progress = ProgressBar()
for i in progress(range(80)):
  time.sleep(0.01)
```

Customizing widgets:
```
widgets = ['Something: ', Percentage(), ' ', Bar(marker=RotatingMarker()),
           ' ', ETA(), ' ', FileTransferSpeed()]
pbar = ProgressBar(widgets=widgets, maxval=10000000).start()
for i in range(1000000):
  # do something
  pbar.update(10*i+1)
pbar.finish()
```

For more examples see: http://code.google.com/p/python-progressbar/source/browse/examples.py