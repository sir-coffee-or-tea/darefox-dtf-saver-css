
# Дополнительные стили и просмотр фотографий и галерей для darefox-dtfsaver
В репозитории есть 2 статьи с примером того, какими стали статьи после добавления style.css и index.js, с помощью которых статьи стали приближены к оригиналу, а также теперь можно просматривать галереи и фото, и увеличивать их.

**style.css** отвечает за стили разных блоков, все они были скопированы из самого DTF(кроме окна просмотра фото), но стили ограничены и должны обновиться, на данный момент style.css изменяет эти блоки:

 1. Текст
 2. Заголовок
 3. Фото и видео (галереи)
 4. Врезка
 5. Статистика сверху(подсайт, автор, время) 
 6. Вставки из twitter и DTF
 
В будущем этот список увеличиться.
**index.js** добавляет возможность просматривать фотографии, для его работы нужно добавить некоторые блоки, об этом можно почитать в разделе **Использование**.

P.S. *я заметил, что в статью нельзя добавить видеоролики из ютуба, хоть как ни пытался, но у меня это не получилось, тут нужен специалист.*

P.S. *ещё стоит удалить этот стиль*

     <style>
        .savedtf-wrapper {
            width: 50%;
            margin: 0 auto;
        }
        * {
            color: black;
            font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
        }
    </style> 

# Использование
Для подключения стилей вам надо добавить файл style.css в папку со статьёй.

Для работы галерей, вам надо изменить иерархию блоков галереи.
Вот как выглядела галерея до изменений:

    <figure class="figure-gallery"> 
     <div class="l-island-c"> 
      <div class="gall">
       <div pos="0">
        <img style="object-fit: contain; width: 100%; height: 100%;" src="img\df79cc06-92a1-5cbf-97e5-c667e6ee4942.png">
       </div>
       <div pos="1">
        <img style="object-fit: contain; width: 100%; height: 100%;" src="img\53666c17-1bea-5eb8-822a-2ada16db8e42.jpeg">
       </div>
       <div pos="2">
        <img style="object-fit: contain; width: 100%; height: 100%;" src="img\bd399328-260b-54f5-af7f-94ad7c263dda.jpeg">
       </div>
       <div pos="3">
        <img style="object-fit: contain; width: 100%; height: 100%;" src="img\d5e5fbc0-0159-520d-ba05-369dde4e7273.jpeg">
       </div>
       <div pos="4">
        <img style="object-fit: contain; width: 100%; height: 100%;" src="img\d5e5fbc0-0159-520d-ba05-369dde4e7273.jpeg">
       </div>
      </div> 
     </div> 
    </figure> 
После изменений:

    <figure class="figure-gallery"> 
     <div class="l-island-c"> 
      <div class="gall gall--5">
       <div pos="0" style="background-image: url('./img/67490380-d9a5-5040-961e-b25add0758d7.jpeg')">
       </div>
       <div pos="1" style="background-image: url('./img/0a0f68d6-5fb3-5a62-8a48-b387aabc8b27.jpeg')">
       </div>
       <div pos="2" style="background-image: url('./img/28e0243a-c105-50cf-a22a-955661405327.png')">
       </div>
       <div pos="3" style="background-image: url('./img/97d23aea-1410-53b9-915e-132506c46006.jpeg')">
       </div>
       <div pos="4" style="background-image: url('./img/ffd06bb3-18b5-5295-9a72-2332a57fa825.jpeg')">
       </div>
       </div>
      </div> 
     </div> 
    </figure>
Пути к изображениям были изменены, надеюсь не составит труда это сделать.
После:

    ./img/bd399328-260b-54f5-af7f-94ad7c263dda.jpeg

До:

    img\bd399328-260b-54f5-af7f-94ad7c263dda.jpeg

## 

А также для работы галереи нужно добавить класс "gall-[**N**]" для div с классом "gall"
***N** - это количество фотографий в галерее, если он превышает число 5, то N всё равно остаётся на числе 5.*

Вот как будет выглядеть галерея с 3 фотографиями:

    <figure class="figure-gallery"> 
     <div class="l-island-c"> 
      <div class="gall gall--3">
       <div pos="0" style="background-image: url('./img/67490380-d9a5-5040-961e-b25add0758d7.jpeg')">
       </div>
       <div pos="1" style="background-image: url('./img/0a0f68d6-5fb3-5a62-8a48-b387aabc8b27.jpeg')">
       </div>
       <div pos="2" style="background-image: url('./img/28e0243a-c105-50cf-a22a-955661405327.png')">
       </div>
      </div> 
     </div> 
    </figure> 
## 
Если количество фотографий в галерее превысит 5, то для фотографии под номером 5(точнее будет значение 4 в аттрибуте "pos"), вам надо добавить аттрибут "data-more", где вы должны указать количество оставшихся фотографий.
К примеру есть 7 фотографий:

    <div pos="4" data-more="+2" style="background-image: url('./img/ffd06bb3-18b5-5295-9a72-2332a57fa825.jpeg')"> </div>
## 
Вот как будет выглядеть галерея с 7 фотографиями:

    <figure class="figure-gallery"> 
     <div class="l-island-c"> 
      <div class="gall gall--5">
       <div pos="0" style="background-image: url('./img/67490380-d9a5-5040-961e-b25add0758d7.jpeg')">
       </div>
       <div pos="1" style="background-image: url('./img/0a0f68d6-5fb3-5a62-8a48-b387aabc8b27.jpeg')">
       </div>
       <div pos="2" style="background-image: url('./img/28e0243a-c105-50cf-a22a-955661405327.png')">
       </div>
       <div pos="3" style="background-image: url('./img/97d23aea-1410-53b9-915e-132506c46006.jpeg')">
       </div>
       <div pos="4" data-more="+2" style="background-image: url('./img/ffd06bb3-18b5-5295-9a72-2332a57fa825.jpeg')">
       </div>
       <div pos="5" style="background-image: url('./img/97d23aea-1410-53b9-915e-132506c46006.jpeg')">
       </div>
       <div pos="6" style="background-image: url('./img/ffd06bb3-18b5-5295-9a72-2332a57fa825.jpeg')">
       </div>
      </div> 
     </div> 
    </figure> 
   ## 
Ещё в конце страницы надо добавить этот код, в этом коде можно ничего не менять, он нужен для просмотра изображений из галереи и одиночной фотографии:

    <div class="modal" style="position: fixed;">
      <div class="modal-bg">
        <div class="modal-container">
          <div class="modal-parent-gl">
            <div class="modal-gl">
              <button class="modal-arrow-left modal-button">
                <img height="50" width="30" class="icon icon_arrow_left" src="svgexport-67.svg"/>
              </button>
              <button class="modal-arrow-right modal-button">
                <img height="50" width="30" class="icon icon_arrow_right" src="svgexport-68.svg"/>
              </button>
              <div class="modal-exit-territory">
                <img class="icon icon_close" src="svgexport-69.svg"/>
              </div>
              <div class="modal-gl-container">
                <div class="gl-image">
                  <input type="checkbox" id="zoomCheck">
                  <label for="zoomCheck">
                    <img class="gl-current-image" src="img\0a0f68d6-5fb3-5a62-8a48-b387aabc8b27.jpeg">
                  </label>
                </div> 
                <div class="gl-footer">
                  <div class="gl-counter">
                     из 
                  </div>
                </div>
                </div>
              </div>
            </div>
          </div>
        </div>
        <div class="modal-instruments">
        </div>
      </div>
    </div>
    <script type="text/javascript" src="index.js"></script>
Что же, теперь всё будет работать, надеюсь это вам помогло! Удачи! take fun!
