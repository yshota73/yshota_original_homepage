//------ローディングから画面遷移------
const loadingAreaGray = document.querySelector('#loading');
const loadingAreaGreen = document.querySelector('#loading-screen');
const loadingText = document.querySelector('#loading p');

window.addEventListener('load', () => { //javascript内で新しいidを設定

    //------ローディング中(グレースクリーン)------
    loadingAreaGray.animate(
        {
            opacity: [1, 0], //透明度（不透明）１→０（透明）
            visibility: 'hidden', //hiddenにしないとグレースクリーンが手前に残り、ボタンを押せない
        },
        {
            duration: 2000, //アニメーションの再生時間
            delay: 1200, //アニメーションが開始するまでの時間
            easing: 'ease', //動きの緩急
            fill: 'forwards', //アニメーションの最後の状態（透明）をキープ
        }
    );

    //------ローディング中(グリーンスクリーン)------
    loadingAreaGreen.animate(
        {
            translate: ['0 100vh', '0 0', '0 -100vh'] //100vh：画面に対して100%
        },
        {
            duration: 2000,
            delay: 800,
            easing: 'ease',
            fill: 'forwards',
        }
    );

    //------ローディング中テキスト------
    loadingText.animate(
        [
            {
                opacity: 1,
                offset: .8  //80%の時間までは不透明度１を維持
            },
            {
                opacity: 0,
                offset: 1  //100%
            },
        ],
        {
            duration: 1200,
            easing: 'ease',
            fill: 'forwards',
        }
    );
});

//------画像ギャラリー------
const mainImage = document.querySelector('.gallery-image img');
const thumbImages = document.querySelectorAll('.gallery-thumbnails img');

thumbImages.forEach((thumbImage) => { //forEach：各画像(thumbImage)に対して行う
    //何が.addEventlistener.(どうなったら,どうなる)
    thumbImage.addEventListener('mouseover', (event) => { //'mouseover',(event)：マウスが乗った画像の情報を渡す、{}：行う処理の内容
        mainImage.src = event.target.src; //いまマウスが乗ってる画像の情報（event.target.src）をmainImageに代入
        mainImage.animate(
            {
                opacity: [0, 1],
                duration: 500,
            }
        )
    });
});

//------ナビゲーションメニュー------
const menuOpen = document.querySelector('#menu-open');
const menuClose = document.querySelector('#menu-close');
const menuPanel = document.querySelector('#menu-panel');
const menuItems = document.querySelectorAll('#menu-panel li');
const menuOptions = {
    duration: 1400,
    easing: 'ease',
    fill: 'forwards',
};

//------メニューを開く------
menuOpen.addEventListener('click', () => { //マウスが乗っている画像、等の情報が不要なため()の中は空
    menuPanel.animate({ translate: ['100vw', 0] }, menuOptions);

    //------リンクをひとつずつ順に表示------
    menuItems.forEach((menuItem, index) => { //index：０から始まる通し番号　　引数が２つ以上あるときは()でくくる
        menuItem.animate(
            {
                opacity: [0, 1],
                translate: ['2rem', 0],
            },
            {
                duration: 2400,
                delay: 300 * index,
                easing: 'ease',
                fill: 'forwards',
            }
        );
    });
});

//------メニューを閉じる------
menuClose.addEventListener('click', () => {
    menuPanel.animate(
        {
            translate: [0, '100vw']
        },
        menuOptions //menuOptionsと書くことでコード量を減らす
    );

    menuItems.forEach((menuItem) => {
        menuItem.animate(
            {
                opacity: [1, 0]
            },
            menuOptions
        );
    });
});

//------監視対象が範囲内に現れたら実行する動作------
const animateFade = (entries, obs) => { //entries：観測した対象のリスト
    entries.forEach((entry) => {
        if (entry.isIntersecting) { //isIntersectiong：本当に現れたら
            entry.target.animate( //.target：対象そのもの
                {
                    opacity: [0, 1],
                    filter: ['blur(.4rem)', 'blur(0)'],
                    translate: ['0 4rem', 0],
                },
                {
                    duration: 2000,
                    easing: 'ease',
                    fill: 'forwards',
                }
            );

            obs.unobserve(entry.target); //一度表示されたら監視をやめる
        }
    });
};

//------監視設定------
const fadeObserver = new IntersectionObserver(animateFade); //newをつけて実際に作動させる

//------.fadeinを監視するよう指示------
const fadeElements = document.querySelectorAll('.fadein');
fadeElements.forEach((fadeElement) => {
    fadeObserver.observe(fadeElement); //fadeObserverに対してfadeElementsの各要素fadeElementを監視するよう指示
});
