# Angular Circular Carousel

> Create customizable Angular2+ Slideshow/ Carousel that can works as a circular slideshow with no constraints on styles.

## Install

```
npm install ng2-slideshow
```

## Usage

Import `CarouselModule` into your module

your-module.module.ts
```
import { CarouselModule } from 'ng2-slideshow';

@NgModule({
  imports: [
    ...
    CarouselModule,
  ],
```
Import `Settings` and `Image` interface into your component class for providing settings configuration and list of Images for your carousel.

your-component.component.ts
```
import { Settings, Image } from 'ng2-slideshow';
...
export class YourComponent {
  settings: Settings;
  images: Image[];
}
```

Settings interface
```
interface Settings { 
    height: String; // Required | Height of carousel in 'px' or percentage.
    width: String; // Required | Width of carousel in 'px' or percentage. 
    carouselDotClass?: String; // Optional | CSS Class for navigator dots at the bottom of carousel, it can be a sprite class or glyphicon or font icon class. If no class is provided, no dots will be shown.
    prevIconClass?: String; // Optional | CSS Class for left navigator icon, it can be a sprite class or glyphicon or font icon class. If no class is provided, no left icon will be shown.
    nextIconClass?: String; // Optional | CSS Class for right navigator icon, it can be a sprite class or glyphicon or font icon class. If no class is provided, no right icon will be shown.
    transitionDuration: Number; // Required | Transition time between bet two slides, animation happens for this duration.
    transitionDelay: Number; // Required | Wait time before automatically move to next slide, i.e animation starts.
}
```

Image interface
```
interface Image { 
    caption: String; // Text to display in alt attribute of `img` tag.
    media: String; // Absolute path for your image.
}
```


It takes two inputs and emits click event to parent component.

Inputs:
```
images: Image[]; //Required | "Array of images, these images will be displayed in carousel";
settings: Settings; //Required | "Settings for the Carousel"
```

Now you can use carousel selector in your component template as shown below

your-component.component.html
```
<ng2-slideshow [IMAGES]="images" [SETTINGS]="settings" (onclick)=handler($event)></ng2-slideshow>
```

It emits onclick event to the parent component, So there should be an event handler in parent component class. $event omits the 'index' of the image that user has clicked. From this handler, You can navigate user to corresponding page or show modal or something else.

## Styling

For styling of carousel, SCSS or CSS can be written as global styles for uniform styling across the project, or you can write styles inside your parent component styles using `/deep/` selector.

**Note**: Please maintain the hierarchy of classes while writing style and don't forget to add `/deep/` before `.carousel-wrapper` in case you are writing styles inside your parent component.

sample.style.scss
```
.carousel-wrapper {
    ...
    .carousel {
        ....
    }
}
```
 
## License

MIT © [Uttam Pratap Choudhary](//https://github.com/uttamchoudhary)
