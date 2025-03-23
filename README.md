<script src="<script>
  // 1. Create a scene
  const scene = new THREE.Scene();

  // 2. Create a camera
  const camera = new THREE.PerspectiveCamera(75, window.innerWidth / window.innerHeight, 0.1, 1000);
  camera.position.z = 5;

  // 3. Create a renderer
  const renderer = new THREE.WebGLRenderer();
  renderer.setSize(window.innerWidth, window.innerHeight);
  document.body.appendChild(renderer.domElement);

  // 4. Add a light
  const light = new THREE.AmbientLight(0xffffff, 1);
  scene.add(light);

  // 5. Create a glass bottle (cylinder shape)
  const geometry = new THREE.CylinderGeometry(0.5, 0.5, 2, 32);
  const material = new THREE.MeshStandardMaterial({ color: 0xffffff, transparent: true, opacity: 0.5 });
  const bottle = new THREE.Mesh(geometry, material);
  scene.add(bottle);

  // 6. Create a liquid inside the bottle
  const liquidGeometry = new THREE.CylinderGeometry(0.49, 0.49, 1, 32);
  const liquidMaterial = new THREE.MeshStandardMaterial({ color: 0x0000ff });
  const liquid = new THREE.Mesh(liquidGeometry, liquidMaterial);
  liquid.position.y = -0.5;
  bottle.add(liquid);

  // 7. Animation loop
  function animate() {
    requestAnimationFrame(animate);
    renderer.render(scene, camera);
  }
  animate();
</script>
"></script>
