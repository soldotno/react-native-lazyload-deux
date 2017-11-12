# react-native-lazyload-deux

A lazyload components suit for React Native.

Forked from [react-native-lazyload](https://github.com/magicismight/react-native-lazyload) as it seems to be no longer maintained.

## Install

```
npm install react-native-lazyload-deux
```


## Usage

### LazyloadScrollView

A lazyload container component based on `ScrollView`

#### Props

* [ScrollView](https://facebook.github.io/react-native/docs/scrollview.html#props).
* `name`: Unique name of scroll view.
* `renderDistance`: Offset of pixels before to start rendering.
* `recycle`:
* `recycleDistance`:
* `horizontal`:

#### Functions

*  `refresh`: Force to trigger an update. Useful after nagivation pop/push where the memory may have been released.

#### Example

```js
import React, { Component } from 'react-native';
import { LazyloadScrollView, LazyloadView, LazyloadImage } from 'react-native-lazyload-deux';

const views = [
  {
    title: 'A view',
    image: 'https://example.org/1.png',
  },
  {
    title: 'Another view',
    image: 'https://example.org/2.png',
  }
];

class LazyloadScrollViewExample extends Component {
  renderViews() {
    return views.map((view, i) => {
      return (
        <LazyloadView
          host="unique-lazyload-list-name"
          key={`lazy-scroll-view-${i}`}
        >
          <Text>{view.title}</Text>
          <LazyloadImage
            host="unique-lazyload-list-name"
            source={view.image}
          />
        </LazyloadView>
      );
    });
  }

  render() {
    return (
      <LazyloadScrollView
        name="unique-lazyload-list-name"
      >
        {this.renderView()}
      </LazyloadScrollView>
    );
  }
}
```

### LazyloadListView

A lazyload container component based on `ListView`. Won't render `LazyloadView` and `LazyloadImage` until they are visible on screen.

#### Props

* [ListView](https://facebook.github.io/react-native/docs/listview.html#props).

#### Functions

*  `refresh`: Force to trigger an update. Useful after nagivation pop/push where the memory may have been released.

#### Example

```js
import React, { Component } from 'react-native';
import { LazyloadScrollView, LazyloadView, LazyloadImage } from 'react-native-lazyload-deux';

const views = [
  {
    title: 'A view',
    image: 'https://example.org/1.png',
  },
  {
    title: 'Another view',
    image: 'https://example.org/2.png',
  }
];

class LazyloadListViewExample extends Component {
  renderViews() {
    return views.map((view, i) => {
      return (
        <LazyloadView
          host="unique-lazyload-list-name"
          key={`lazy-list-view-${i}`}
        >
          <Text>{view.title}</Text>
          <LazyloadImage
            host="unique-lazyload-list-name"
            source={view.image}
          />
        </LazyloadView>
      );
    });
  }

  render() {
    return (
      <LazyloadListView
        name="unique-lazyload-list-name"
      >
        {this.renderView()}
      </LazyloadListView>
    );
  }
}
```

### LazyloadView

Based on View component. This component's content won't be rendered util it scrolls into sight. It should be inside a `LazyloadScrollView` or `LazyloadListView` which has the same `name` prop as this component's host prop.

#### Props

* [View](https://facebook.github.io/react-native/docs/view.html#props).
* `host`: The unique name of it's container
* `onVisibilityChange`: Callback for when the view is visible.
* `animation`: Lazyload animation

#### Example

See either example above.

### LazyloadImage

Based on Image component. The image content won't be rendered util it scrolls into sight. It should be inside a `LazyloadScrollView` or `LazyloadListView` which has the same `name` prop as this component's host prop.

#### Props

* [Image](https://facebook.github.io/react-native/docs/image.html#props).
* `host`: The unique name of it's container
* `animation`: Lazyload animation

#### Example

See either example above.

## Complete example

Clone this repository from Github and cd to 'Example' directory then run `npm install`.

